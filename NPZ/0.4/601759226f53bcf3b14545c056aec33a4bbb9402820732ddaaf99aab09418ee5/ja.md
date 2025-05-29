```
npzread(filename::AbstractString, [vars])
```

`filename` から変数または変数のコレクションを読み込みます。入力は `npy` または `npz` ファイルである必要があります。オプションの引数 `vars` は `npz` ファイルのみに使用されます。指定された場合、ファイルから一致する変数のみが読み込まれます。

!!! note "ゼロ次元配列"
    ゼロ次元配列は読み込まれる際にストリップされ、その中に含まれる値が返されます。これは、数値が書き出され、ゼロ次元配列として再読み込みされるnumpyとの顕著な違いです。


# 例

```julia
julia> npzwrite("temp.npz", x = ones(3), y = 3)

julia> npzread("temp.npz") # すべての変数を読み込む
Dict{String,Any} with 2 entries:
  "x" => [1.0, 1.0, 1.0]
  "y" => 3

julia> npzread("temp.npz", ["x"]) # "x" のみを読み込む
Dict{String,Array{Float64,1}} with 1 entry:
  "x" => [1.0, 1.0, 1.0]
```
