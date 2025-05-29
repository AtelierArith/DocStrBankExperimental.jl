```
getkeypath(x, kp::KeyPath)
```

Return the value in `x` at the path `kp`.

See also [`KeyPath`](@ref), [`haskeypath`](@ref), and [`setkeypath!`](@ref).

# Examples

```jldoctest
julia> x = Dict(:a => 3, :b => Dict(:c => 4, "d" => [5, 6, 7]))
Dict{Symbol, Any} with 2 entries:
  :a => 3
  :b => Dict{Any, Any}(:c=>4, "d"=>[5, 6, 7])

julia> getkeypath(x, KeyPath(:b, "d", 2))
6
```
