```
shift(domain::CartesianIndices{N}, axes::NTuple{N2,Int}, n::NTuple{N2,Int}
```

) where {N,N2}

指定された `axes` のセットに対して `n` だけ `CartesianIndices` ドメインをシフトします。
