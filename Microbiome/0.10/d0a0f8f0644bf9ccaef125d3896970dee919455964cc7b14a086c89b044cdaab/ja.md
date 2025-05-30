```
rankfilter(comm::AbstractAbundanceTable, cl::Union{Symbol, Int}; keepempty=false)
```

`comm`のコピーを返します。ここで、`taxrank(feature) == cl`を満たす行のみが保持されます。`keepempty = true`を使用すると、`rank`を持たない特徴（例："UNIDENTIFIED"）も保持されます。
