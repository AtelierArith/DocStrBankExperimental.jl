```julia
midpointquadrature(bincenters, values)
```

中点積分を使用して、`values`のベクトルで指定されたy位置と`bincenters`のベクトルで指定されたx位置の下の面積を合計します。

### 例

```julia
julia> midpointquadrature(0:0.1:10, 0:0.1:10)
50.5
```
