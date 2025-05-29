```
GeoTable(domain; vtable, etable)
```

`domain`から空間ジオテーブルを作成し、頂点のジオテーブルを持つテーブル`vtable`と、要素のジオテーブルを持つテーブル`etable`を指定します。

## 例

```julia
GeoTable(CartesianGrid(10,10),
  etable = (temperature=rand(100), pressure=rand(100))
)
```
