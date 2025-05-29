```
create_model_from_config(
    config_file::AbstractString, configmodel::AbstractString;
    modelpars::Dict = Dict()
) -> model::Model

create_model_from_config(
    config_files,
    configmodel::AbstractString;
    modelpars::Dict = Dict()
) -> model::Model
```

Construct model from a single [YAML](https://en.wikipedia.org/wiki/YAML) `config_file`, or from a collection of `config_files`,  which are read in order and concatenated before being parsed as yaml.

Optional argument `modelpars` provides parameters that override those in `<configmodel>:` `parameters:` section.
