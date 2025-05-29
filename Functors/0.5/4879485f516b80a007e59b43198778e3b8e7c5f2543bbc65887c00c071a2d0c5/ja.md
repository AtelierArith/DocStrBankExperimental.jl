```
getkeypath(x, kp::KeyPath)
```

`kp`のパスにある`x`の値を返します。

関連情報として[`KeyPath`](@ref)、[`haskeypath`](@ref)、および[`setkeypath!`](@ref)を参照してください。

# 例

```jldoctest
julia> x = Dict(:a => 3, :b => Dict(:c => 4, "d" => [5, 6, 7]))
Dict{Symbol, Any} with 2 entries:
  :a => 3
  :b => Dict{Any, Any}(:c=>4, "d"=>[5, 6, 7])

julia> getkeypath(x, KeyPath(:b, "d", 2))
6
```
