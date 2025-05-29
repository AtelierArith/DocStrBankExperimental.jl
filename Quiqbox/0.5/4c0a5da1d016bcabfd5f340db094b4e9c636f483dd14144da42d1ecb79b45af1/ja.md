```
hasApprox(obj1, obj2, obj3...; ignoreFunction::Bool=false, ignoreContainer::Bool=false,
          decomposeNumberCollection::Bool=false, atol::Real=1e-15) -> 
Bool
```

[`hasEqual`](@ref)と似ていますが、比較されるコンテナの`Number`型フィールド（例：`Float64`）が正確に同じ値を持つ必要はなく、むしろ`atol`によって決定される誤差の閾値内の近似値を持つ必要があります。これは`isapprox`のように動作します。
