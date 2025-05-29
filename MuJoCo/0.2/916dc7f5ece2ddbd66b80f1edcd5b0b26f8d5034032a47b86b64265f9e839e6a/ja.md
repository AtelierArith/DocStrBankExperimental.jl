```
mj_ray(m, d, pnt, vec, geomgroup, flg_static, bodyexclude, geomid)
```

可視ジオメトリと交差するレイ (pnt+x*vec, x>=0) を、bodyexclude に含まれるジオメトリを除外して計算します。最も近い表面までの距離 (x) を返し、交差がない場合は -1 を返し、出力 geomid を返します。geomgroup、flg_static は mjvOption と同様です; geomgroup==NULL の場合はグループ除外をスキップします。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`** -> 定数。
  * **`pnt::Vector{Float64}`** -> サイズ 3 のベクトル。`pnt` はサイズ 3 のベクトルである必要があります。定数。
  * **`vec::Vector{Float64}`** -> サイズ 3 のベクトル。`vec` はサイズ 3 のベクトルである必要があります。定数。
  * **`geomgroup::Vector{UInt8}`** -> **オプション**のサイズ 6 のベクトル。`geomgroup` はサイズ 6 のベクトルである必要があります。必要ない場合は `nothing` に設定できます。定数。
  * **`flg_static::UInt8`**
  * **`bodyexclude::Int32`**
  * **`geomid::Vector{Int32}`** -> サイズ 1 のベクトル。`geomid` はサイズ 1 のベクトルである必要があります。
