```
npzwrite(filename::AbstractString, vars::Dict{<:AbstractString})
npzwrite(filename::AbstractString, args...; kwargs...)
```

最初の形式では、`vars`内の変数を`filename`という名前の`npz`ファイルに書き込みます。

2番目の形式では、`args`と`kwargs`内の変数を収集し、それらをすべて`filename`に書き込みます。`args`内の変数は`arr_0`、`arr_1`などの名前で保存され、`kwargs`内のものは指定された名前で保存されます。

`numpy`とは異なり、拡張子`.npz`は`filename`に追加されません。

!!! warn "警告"
    同じ名前の既存のファイルは上書きされます。


# 例

```julia
julia> npzwrite("temp.npz", Dict("x" => ones(3), "y" => 3))

julia> npzread("temp.npz")
Dict{String,Any} with 2 entries:
  "x" => [1.0, 1.0, 1.0]
  "y" => 3

julia> npzwrite("temp.npz", ones(2,2), x = ones(3), y = 3)

julia> npzread("temp.npz")
Dict{String,Any} with 3 entries:
  "arr_0" => [1.0 1.0; 1.0 1.0]
  "x"     => [1.0, 1.0, 1.0]
  "y"     => 3
```
