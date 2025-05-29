```
define_configuration([args,] cfg, defaults::Dict)
define_configuration([args,] cfg, fname::String)
```

Creates a ArgParse Settings from `cfg` which is created using `Configurations.@cfg`. The initial values / defaults can be specified using a dictionary (See `Configurations.from_dict` for how to specify that). The other cfg is to pass a path to a configuration file which can be of type – `toml`, `yml` or `json`.
