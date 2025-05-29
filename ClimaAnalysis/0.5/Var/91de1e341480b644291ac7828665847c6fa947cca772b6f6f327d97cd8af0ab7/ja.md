```
read_var(paths::Vector{String}; short_name = nothing)
```

NetCDFファイルのベクターから`short_name`変数を読み取ります。

この関数は、時間次元に沿ってNetCDFファイルを自動的に集約します。これが不可能な場合は、エラーがスローされます。OutputVarの属性は、最初のNetCDFファイルの属性と同じです。

`short_name`が`nothing`の場合、変数の名前を自動的に特定します。複数の変数が存在する場合は、アルファベット順で最後のものが選択されます。

属性の中に`units`が含まれている場合、それを解析し、[`Unitful`](https://painterqubits.github.io/Unitful.jl)オブジェクトに変換しようとします。`Unitful`を持つ`OutputVar`は、自動単位変換をサポートします。

`units`を文字列としてアクセスしたい場合は、[`units`](@ref)関数を参照してください。

# 例

```julia
simdir = SimDir("my_output")
read_var(simdir.variable_paths["hu"]["inst"])

read_var(["my_netcdf_file1.nc", "my_netcdf_file2.nc"], short_name = "ts")
```
