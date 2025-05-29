```
run_model(configfile::AbstractString, configname::AbstractString; call_do_deriv=true, tforce=0.0, logger=Logging.NullLogger())
run_model(model::Model; call_do_deriv=true, tforce=0.0, logger=Logging.NullLogger())
```

For use in @PrecompileTools.compile*workload: create*model*from*config and optionally call do_deriv at time tforce
