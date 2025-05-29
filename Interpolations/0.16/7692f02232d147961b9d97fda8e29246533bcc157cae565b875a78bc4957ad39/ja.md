```
knotsbetween(iter; start, stop)
knotsbetween(iter, start, stop)
```

`iter`のすべてのノットを反復処理し、`start < k < stop`となるようにします。

`iter`は`AbstractInterpolation`であるか、`knots`の出力（つまり、`KnotIterator`または`KnotIterator`をラップした`ProductIterator`）である可能性があります。

`start`が指定されていない場合、反復は最初のノットから始まります。`start`と`stop`の両方が指定されていない場合、`ArgumentError`が発生します。

そのようなノットが存在しない場合、長さ0のKnotIteratorが返されます。

# 例

```jldoctest
julia> etp = linear_interpolation([1.0, 1.2, 2.3, 3.0], rand(4); extrapolation_bc=Periodic());

julia> knotsbetween(etp; start=38, stop=42) |> collect
6-element Vector{Float64}:
 38.3
 39.0
 39.2
 40.3
 41.0
 41.2
```
