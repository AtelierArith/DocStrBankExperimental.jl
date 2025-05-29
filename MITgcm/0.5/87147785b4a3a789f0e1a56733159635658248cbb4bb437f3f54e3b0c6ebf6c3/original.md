```
MITgcm_namelist(groups,params)
```

Data structure representing a MITgcm *namelist* file, such as `data.pkg`, which contains 

```
    groups :: Array{Symbol,1} = Array{Symbol,1}(undef, 0)
    params :: Array{OrderedDict{Symbol,Any},1} = Array{OrderedDict{Symbol,Any},1}(undef, 0)
```

with model parameters (`params`) being organized in `groups` as done in the files.

```
using MITgcm
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read_namelist(fil)
MITgcm_namelist(nml.groups,nml.params)
MITgcm_namelist(groups=nml.groups,params=nml.params)
MITgcm_namelist(groups=nml.groups)
```
