```
read_toml(config_name::Symbol)
```

Read toml parameter file specified by configuration name.

```
using MITgcm
params=read_toml(:OCCA2)
```
