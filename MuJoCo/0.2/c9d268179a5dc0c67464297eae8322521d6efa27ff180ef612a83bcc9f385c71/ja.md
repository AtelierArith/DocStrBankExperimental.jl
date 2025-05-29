```
mj_geomDistance(m, d, geom1, geom2, distmax, fromto)
```

2つのジオメトリ間の最小の符号付き距離を返し、オプションでgeom1からgeom2へのセグメントを返します。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`** -> 定数。
  * **`geom1::Int32`**
  * **`geom2::Int32`**
  * **`distmax::Float64`**
  * **`fromto::Matrix{Float64}`** -> **オプション**の可変サイズの行列。`fromto`はサイズ6である必要があります。必要ない場合は`nothing`に設定できます。
