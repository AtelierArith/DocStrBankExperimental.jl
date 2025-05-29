```
read_namelist(fil)
```

Read a `MITgcm` namelist file in native format, parse it, and return as a `NamedTuple`.

```
using MITgcm
testreport(MITgcm_config(configuration="advect_xy"))
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
namelist=read_namelist(fil)
```
