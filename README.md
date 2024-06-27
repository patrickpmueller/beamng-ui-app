# beamng-ui-app
**aimed @self**

## Doc links
 - https://wiki.beamng.com/Streams.html#wheelInfo
 - https://documentation.beamng.com/modding/ui/app_creation/
 - AngluarJS Docs

## File structure
```
appname/
└── ui/
    └── modules/
        └── apps/
            └── appname/
                ├── app.js
                ├── app.json
                └── app.png
```

## Activate UI App
- https://documentation.beamng.com/getting_started/user_interface/

# AI Driving 
- https://documentation.beamng.com/tutorials/ai/
- https://www.beamng.com/threads/ai-settings-explained.51733/#post-781006

## BeamNGPy
 - https://github.com/BeamNG/BeamNGpy
 - https://beamngpy.readthedocs.io
```
conda install beamngpy -c conda-forge
pip install beamngpy
```

./BeamNG.tech.x64 -console -nosteam -tcom-listen-ip 127.0.0.1 -lua extensions.load('tech/techCore');tech_techCore.openServer(64256)

Python API test connection
```
from beamngpy import BeamNGpy, Scenario, Vehicle
from beamngpy.sensors import PowertrainSensor
from time import sleep
beamng = BeamNGpy('192.168.1.202', 64256)
beamng.open()
scenario = Scenario('west_coast_usa', 'powertrain_analysis')
careful = Vehicle('careful', model='etk800', license='CAREFUL', color='Green')
aggressive = Vehicle('aggressive', model='etk800', license='AGGRO', color='Red')
# Add it to our scenario at this position and rotation
scenario.add_vehicle(careful, pos=(-767.1, 402.8, 142.8), rot_quat=(0, 0, 0.027, 1))
scenario.add_vehicle(aggressive, pos=(-770.1, 398.8, 142.8), rot_quat=(0, 0, 0.027, 1))

scenario.make(beamng)
beamng.scenario.load(scenario)
beamng.settings.set_deterministic()
beamng.settings.set_steps_per_second(60)
beamng.scenario.start()

careful_pt = PowertrainSensor('careful_sensor', beamng, careful, is_send_immediately=False, physics_update_time=0.001)
aggressive_pt = PowertrainSensor('aggressive_sensor', beamng, aggressive, is_send_immediately=False,
                                 physics_update_time=0.001)

```
