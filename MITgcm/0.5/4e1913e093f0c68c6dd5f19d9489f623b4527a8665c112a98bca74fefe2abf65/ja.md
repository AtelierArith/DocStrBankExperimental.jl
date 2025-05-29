```
write_all_namelists(params,output_path=tempname())
```

すべての `MITgcm` namelist を `output_path` にファイルとして書き込みます。対応する `toml file` から。

```
using MITgcm
params=read_toml(:OCCA2)
write_all_namelists(params)
```
