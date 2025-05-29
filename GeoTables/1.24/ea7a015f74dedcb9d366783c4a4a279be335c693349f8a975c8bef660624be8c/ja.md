```
GeoTable(domain, values)
```

`domain` とジオテーブル `values` の辞書。各ランク `r`（またはパラメトリック次元）に対して、対応する Tables.jl テーブル `values[r]` が存在する可能性があります。

## 例

```julia
# グリッド要素に温度と圧力を付加する
GeoTable(CartesianGrid(10,10),
  Dict(2 => (temperature=rand(100), pressure=rand(100)))
)
```
