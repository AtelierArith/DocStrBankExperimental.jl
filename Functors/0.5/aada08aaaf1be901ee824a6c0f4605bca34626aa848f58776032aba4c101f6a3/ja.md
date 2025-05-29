```
haskeypath(x, kp::KeyPath)
```

`x`がパス`kp`に値を持っている場合は`true`を返します。

関連情報として[`KeyPath`](@ref)、[`getkeypath`](@ref)、および[`setkeypath!`](@ref)を参照してください。

# 例

```jldoctest
julia> x = Dict(:a => 3, :b => Dict(:c => 4, "d" => [5, 6, 7]))
Dict{Symbol, Any} with 2 entries:
  :a => 3
  :b => Dict{Any, Any}(:c=>4, "d"=>[5, 6, 7])

julia> haskeypath(x, KeyPath(:a))
true

julia> haskeypath(x, KeyPath(:b, "d", 1))
true

julia> haskeypath(x, KeyPath(:b, "d", 4))
false
```
