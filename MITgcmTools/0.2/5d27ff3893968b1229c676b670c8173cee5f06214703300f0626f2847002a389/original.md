```
setup(config::MITgcm_config)
```

Create a `run/` folder and link everything there as needed to be ready to run model as  normally done for most-standard MITgcm configurations (incl. `prepare_run` and `mitgcmuv`). Call `ClimateModels.git_log_init(config)` to setup git tracker and  `put!(config.channel,MITgcm_launch)` to be executed via `launch(config)` later.

(part of the climate model interface as specialized for `MITgcm`)
