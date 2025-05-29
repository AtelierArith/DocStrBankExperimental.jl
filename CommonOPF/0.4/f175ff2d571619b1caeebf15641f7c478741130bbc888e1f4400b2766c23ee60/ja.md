```
add_time_vector_variables!(
    m::JuMP.AbstractModel, 
    net::Network{SinglePhase}, 
    var_symbol::Symbol, 
    indices::AbstractVector{T} 
) where {T}
```

`m.obj_dict`に変数を追加します。インデックスは次の通りです：

1. `var_symbol` は `:v` のように
2. `indices` は通常、バスインデックス用の `Vector{String}` またはエッジインデックス用の `Vector{Tuple{String, String}}`（例えば `("bus1", "bus2")`）です
3. タイムステップは `1:net.Ntimesteps` です

例えば、エッジ変数 `:sij` の一つのエッジ `("bus1", "bus2")` の電圧変数をタイムステップ `5` でアクセスするには、次のようにします：

```julia
m[:sij][("bus1", "bus2")][5]
```
