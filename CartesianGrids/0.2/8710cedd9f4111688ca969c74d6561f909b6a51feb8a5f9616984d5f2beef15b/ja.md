```
TensorData <: PointData
```

2x2 テンソル値データの1次元配列のラッパーで、フィールド `dudx`、`dudy`、`dvdx`、`dvdy` を持ちます。結果として得られるラッパーは、これら4つのコンポーネントが重ねられているかのようにインデックス指定できます。

# コンストラクタ

  * `TensorData(d::AbstractVector[,dtype=Float64])` は、データ `d` の1次元配列のラッパーを構築し、`d` を4つのコンポーネントに均等に分割します。
  * `TensorData(dudx,dudy,dvdx,dvdy)` は、各々が `AbstractVector` 型のテンソルコンポーネントデータのラッパーを構築します。
  * `TensorData(n::Int)` は、すべてのコンポーネントの長さ `n` のゼロで構成されたラッパーを構築します。
  * `TensorData(x::PointData[,dtype=Float64])` は、`x` によってラップされたものと同じ長さのゼロコンポーネントのラッパーを構築します。

# 例
