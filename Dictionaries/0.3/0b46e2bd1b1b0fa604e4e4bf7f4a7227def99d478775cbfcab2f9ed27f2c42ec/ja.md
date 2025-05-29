```
Dictionary(indices, undef::UndefInitializer)
```

`indices` の iterable から `Dictionary` を構築します。値は未定義/初期化されていません。

# 例

```julia
julia> Dictionary{Int, Float64}([1,2,3], undef)
3-element Dictionary{Int64,Float64}
 1 │ 6.9220016379355e-310
 2 │ 6.9220016379426e-310
 3 │ 6.92200163794736e-310
```
