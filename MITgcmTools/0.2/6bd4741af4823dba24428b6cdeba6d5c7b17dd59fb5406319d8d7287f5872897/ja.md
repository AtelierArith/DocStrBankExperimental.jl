```
MITgcm_namelist(groups,params)
```

MITgcm *namelist* ファイルを表すデータ構造で、例えば `data.pkg` のように、以下を含みます。

```
    groups :: Array{Symbol,1} = Array{Symbol,1}(undef, 0)
    params :: Array{OrderedDict{Symbol,Any},1} = Array{OrderedDict{Symbol,Any},1}(undef, 0)
```

モデルパラメータ (`params`) は、ファイル内で行われているように `groups` に整理されています。

```
using MITgcmTools
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read_namelist(fil)
MITgcm_namelist(nml.groups,nml.params)
MITgcm_namelist(groups=nml.groups,params=nml.params)
MITgcm_namelist(groups=nml.groups)
```
