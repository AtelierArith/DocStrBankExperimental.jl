```
read_namelist(fil)
```

Read a `MITgcm` namelist file, parse it, and return as a NamedTuple

```
using MITgcmTools
testreport("advect_xy")
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
namelist=read_namelist(fil)
```
