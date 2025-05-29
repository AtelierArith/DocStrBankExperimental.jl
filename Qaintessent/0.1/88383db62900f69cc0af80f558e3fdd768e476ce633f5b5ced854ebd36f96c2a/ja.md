```
num_wires(::AbstractGate)
```

は、AbstractGateオブジェクトによって影響を受けるワイヤの数を返します。

# 例

```jldoctest
julia> num_wires(X)
1

julia> num_wires(SwapGate())
2
```
