```
pbox( x :: Array{Interval{T}, 1} ) where T <: Real
```

等しい質量を持つ区間の配列からpboxを構築します。左端と右端の境界は、cdf境界を構築するためにソートされます。
