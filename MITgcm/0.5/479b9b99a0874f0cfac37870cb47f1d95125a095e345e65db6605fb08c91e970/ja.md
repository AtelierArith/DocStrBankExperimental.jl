```
write_namelist(fil)
```

`MITgcm` の namelist ファイルを保存します（ネイティブフォーマット）。以下の例では、ファイルから読み込み、修正し、write_namelist を使用して新しいファイルに保存します。

```
using MITgcm
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
nml=read(fil,MITgcm_namelist())
write(fil*"_new",nml)
```

または `write_namelist(fil*"_new",namelist)`。
