```
write_namelist(fil)
```

Save a `MITgcm` namelist file. In the example below, one is read from file, modified, and then saved to a new file using write_namelist.

```
using MITgcmTools
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read_namelist(fil)
write_namelist(fil*"_new",namelist)
```

or

```
nml=read(fil,MITgcm_namelist())
write(fil*"_new",nml)
```
