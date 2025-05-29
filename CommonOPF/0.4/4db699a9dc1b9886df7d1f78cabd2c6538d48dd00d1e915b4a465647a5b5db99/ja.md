```
sj_per_unit(j::String, net::Network{MultiPhase})::Tuple{Vector{Vector{<:Real}}, Vector{Vector{<:Real}}}
```

リアルおよびリアクティブパワー注入を、3相インデックスとnet.Ntimesteps時間インデックスを持つベクトルとして返します。例えば：

```julia
Pj, Qj = sj_per_unit(my_bus, net)
...
Pj[phase][time_step]
```
