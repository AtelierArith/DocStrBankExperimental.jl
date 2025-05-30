```
run_model(configfile::AbstractString, configname::AbstractString; call_do_deriv=true, tforce=0.0, logger=Logging.NullLogger())
run_model(model::Model; call_do_deriv=true, tforce=0.0, logger=Logging.NullLogger())
```

@PrecompileTools.compile*workloadの使用のため: configからモデルを作成し、オプションで時刻tforceでdo_derivを呼び出す
