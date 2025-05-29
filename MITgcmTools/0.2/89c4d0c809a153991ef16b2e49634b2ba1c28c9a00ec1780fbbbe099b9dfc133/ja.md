```
write_namelist(fil)
```

`MITgcm` の namelist ファイルを保存します。以下の例では、ファイルから読み込み、修正し、write_namelist を使用して新しいファイルに保存します。

```
using MITgcmTools
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read_namelist(fil)
write_namelist(fil*"_new",namelist)
```

または

```
nml=read(fil,MITgcm_namelist())
write(fil*"_new",nml)
```
