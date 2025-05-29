```
read_all_namelists(input_path)
```

Read all `MITgcm` namelist files in `input_path`, parse them, and return as a NamedTuple of NamedTuples.

```
using MITgcm; path0=default_path()
input_path=joinpath(path0,"verification","advect_xy","input")
params=read_all_namelists(input_path)
```
