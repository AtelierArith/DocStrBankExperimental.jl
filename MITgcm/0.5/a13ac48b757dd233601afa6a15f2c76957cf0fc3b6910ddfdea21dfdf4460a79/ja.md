```
read_toml(toml_file::String)
```

TOMLパラメータファイルをSymbolキーを持つOrderedDictに読み込みます。これは`tracked_parameters.toml`と一致します。

```
using MITgcm, TOML
pth=joinpath(dirname(pathof(MITgcm)),"..","examples","configurations")
toml_file=joinpath(pth,"tutorial_held_suarez_cs.toml")
params=read_toml(toml_file)
```

パラメータをファイルに書き込むのは簡単です。例えば：

```
MC=MITgcm_config(configuration="tutorial_held_suarez_cs")
setup(MC)
open(tempname()*".toml", "w") do io
    TOML.print(io, MC.inputs)
end
```
