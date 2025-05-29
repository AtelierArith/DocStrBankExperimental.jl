```
write_namelist(fil)
```

Save a `MITgcm` namelist file (native format). In the example below, one is read from file, modified, and then saved to a new file using write_namelist.

```
using MITgcm
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read(fil,MITgcm_namelist())
write(fil*"_new",nml)
```

or `write_namelist(fil*"_new",namelist)`.
