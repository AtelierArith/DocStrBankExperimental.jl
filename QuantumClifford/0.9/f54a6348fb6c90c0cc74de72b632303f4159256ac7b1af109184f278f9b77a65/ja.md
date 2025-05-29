ゲートインデックスを[`graphstate`](@ref)からゲートのシーケンスに変換するヘルパー関数。

```jldoctest
julia> s = S" XXX
              YZ_
             -_ZZ";


julia> graph, h_idx, ip_idx, z_idx = graphstate(s);


julia> gates = graph_gatesequence(h_idx, ip_idx, z_idx);


julia> for gate in vcat(gates...) apply!(s, gate) end


julia> s # これは今やグラフ状態です（行1を行2で掛ける必要があることに注意してください）
+ YYZ
+ XZ_
+ _ZX

julia> canonicalize!(s) == canonicalize!(Stabilizer(graph))
true
```

参照: [`graph_gatesequence`](@ref)
