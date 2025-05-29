```
RingAttributions{D} <: AbstractVector{RingIncluding{D}}
```

`PeriodicGraph{D}`のリングの集合を表します。

タイプ`RingAttributions{D}`の`ra`に対して、`ra[i]`は`PeriodicVertex{D}(i)`を含むリングの集合を表す[`RingIncluding{D}`](@ref)オブジェクトです。
