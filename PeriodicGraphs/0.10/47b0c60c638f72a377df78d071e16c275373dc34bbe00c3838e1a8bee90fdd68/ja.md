```
RingAttributions(g::PeriodicGraph{D}, [strong::Bool=false,] [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

`g`のリングを`RingAttributions`にソートして返します。

`strong`が設定されている場合、強いリングのみが保持されます。他の引数の意味については[`rings`](@ref)を参照してください。
