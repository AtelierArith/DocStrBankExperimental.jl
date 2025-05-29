```
function write_configuration(filename::String, brkga_data::BrkgaData,
                             external_params::ExternalControlParams =
                                                    ExternalControlParams())
```

Write the parameters from `brkga_data.params` and `external_params` into `filename`.

# Throws

  * `SystemError`: in case the configuration files cannot be openned.
