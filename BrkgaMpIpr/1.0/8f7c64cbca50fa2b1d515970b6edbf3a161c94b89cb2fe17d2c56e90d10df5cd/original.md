```
load_configuration(configuration_file::String)::
        Tuple{BrkgaParams, ExternalControlParams}
```

Load the parameters from `configuration_file` returning them as a tuple.

# Throws

  * `LoadError`: in cases of the file is an invalid configuration file, parameters are missing, or parameters are ill-formatted.
