```
read_namelist(fil)
```

`MITgcm` の名前リストファイルをネイティブ形式で読み込み、解析して `NamedTuple` として返します。

```
using MITgcm
testreport(MITgcm_config(configuration="advect_xy"))
fil=joinpath(MITgcm_path[1],"verification","advect_xy","run","data")
namelist=read_namelist(fil)
```
