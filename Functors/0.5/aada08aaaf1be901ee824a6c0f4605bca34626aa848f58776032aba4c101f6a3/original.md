```
haskeypath(x, kp::KeyPath)
```

Return `true` if `x` has a value at the path `kp`.

See also [`KeyPath`](@ref), [`getkeypath`](@ref), and [`setkeypath!`](@ref).

# Examples

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
