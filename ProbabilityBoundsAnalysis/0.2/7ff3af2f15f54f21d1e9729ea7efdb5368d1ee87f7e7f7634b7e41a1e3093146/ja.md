```
pbox( x :: Array{Interval{T}, 1} ) where T <: Real
```

等質の区間の配列からpboxを構築します。左端と右端の境界は、cdfの境界を構築するためにソートされます。
