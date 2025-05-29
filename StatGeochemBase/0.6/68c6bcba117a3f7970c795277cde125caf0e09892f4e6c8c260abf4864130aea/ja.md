```julia
trapezoidalquadrature(edges, values)
```

トラペゾイダル積分を使用して、`values`のベクトルで指定されたy位置の下の面積を、`edges`のベクトルで指定されたx位置を使って合計します。ビンは均等に配置されている必要はありませんが、均等に配置されていると助かります（`edges`がAbstractRangeとして指定されている場合、積分は速くなります）。

### 例

```julia
julia> trapezoidalquadrature(0:0.1:10, 0:0.1:10)
50.0
```
