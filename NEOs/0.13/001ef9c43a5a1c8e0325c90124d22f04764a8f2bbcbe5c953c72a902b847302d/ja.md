```
issinglearc(radec::Vector{RadecMPC{T}}, arc::Day = Day(30)) where {T <: Real}
```

`radec`が単一の観測アークであるかどうかを確認します。すなわち、2つの連続した観測が`arc`日以上離れていないことを確認します。この関数は`radec`がソートされていることを前提としています。
