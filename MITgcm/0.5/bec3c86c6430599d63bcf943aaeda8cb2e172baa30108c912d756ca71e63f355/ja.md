```
read_all_namelists(input_path)
```

`input_path`にあるすべての`MITgcm`ナメリストファイルを読み込み、解析して、NamedTupleのNamedTuplesとして返します。

```
using MITgcm; path0=default_path()
input_path=joinpath(path0,"verification","advect_xy","input")
params=read_all_namelists(input_path)
```
