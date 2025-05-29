```
scan_rundir(config::MITgcm_config)
```

Scan a MITgcm run directory (joinpath(MC,"run")) and then, if found, the standard output text file ("output.txt" or "STDOUT.0000") via `scan_stdout`.
