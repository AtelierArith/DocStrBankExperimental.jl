```
read_namelist(fil)
```

`MITgcm` のナメリストファイルを読み込み、解析して NamedTuple として返します。

```
using MITgcmTools
testreport("advect_xy")
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
namelist=read_namelist(fil)
```
