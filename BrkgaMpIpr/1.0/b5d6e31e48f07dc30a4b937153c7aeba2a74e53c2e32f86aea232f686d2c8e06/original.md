```
function write_configuration(filename::String, brkga_params::BrkgaParams,
                             external_params::ExternalControlParams)
```

Write `brkga_params` and `external_params` into `filename`.

# Throws

  * `SystemError`: in case the configuration files cannot be openned.
