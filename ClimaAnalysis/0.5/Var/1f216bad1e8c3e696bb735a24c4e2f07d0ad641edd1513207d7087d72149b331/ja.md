```
read_var(path::String; short_name = nothing)
```

指定されたNetCDFファイル内の`short_name`変数を読み取ります。

`short_name`が`nothing`の場合、変数の名前を自動的に特定します。複数の変数が存在する場合は、アルファベット順で最後のものが選択されます。

`units`が属性の中にある場合、それを解析し、[`Unitful`](https://painterqubits.github.io/Unitful.jl)オブジェクトに変換しようとします。`Unitful`をサポートする`OutputVar`は、自動的な単位変換を行います。

`units`を文字列としてアクセスしたい場合は、[`units`](@ref)関数を参照してください。

# 例

```julia
simdir = SimDir("my_output")
read_var(simdir.variable_paths["hu"]["inst"])

read_var("my_netcdf_file.nc", short_name = "ts")
```
