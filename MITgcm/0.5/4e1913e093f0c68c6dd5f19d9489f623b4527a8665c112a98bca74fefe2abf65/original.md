```
write_all_namelists(params,output_path=tempname())
```

Write all `MITgcm` namelist to files in `output_path`, from corresponding `toml file`

```
using MITgcm
params=read_toml(:OCCA2)
write_all_namelists(params)
```
