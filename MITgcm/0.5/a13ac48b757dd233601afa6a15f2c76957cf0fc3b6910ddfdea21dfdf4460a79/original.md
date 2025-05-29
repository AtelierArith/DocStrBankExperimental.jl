```
read_toml(toml_file::String)
```

Read toml parameter file into an OrderedDict with Symbol keys, consistent with `tracked_parameters.toml`.

```
using MITgcm, TOML
pth=joinpath(dirname(pathof(MITgcm)),"..","examples","configurations")
toml_file=joinpath(pth,"tutorial_held_suarez_cs.toml")
params=read_toml(toml_file)
```

Writing parameters to file is straightforward. For example:

```
MC=MITgcm_config(configuration="tutorial_held_suarez_cs")
setup(MC)
open(tempname()*".toml", "w") do io
    TOML.print(io, MC.inputs)
end
```
