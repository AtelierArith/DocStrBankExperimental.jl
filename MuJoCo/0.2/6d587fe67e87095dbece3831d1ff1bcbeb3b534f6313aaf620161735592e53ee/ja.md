```
mj_multiRay(m, d, pnt, vec, geomgroup, flg_static, bodyexclude, geomid, dist, nray, cutoff)
```

単一の点から放射される複数の光線を交差させます。mj_rayと似た意味を持ちますが、vecは(nray x 3)の方向の配列です。

# 引数

  * **`m::Model`** -> 定数。
  * **`d::Data`**
  * **`pnt::Vector{Float64}`** -> サイズ3のベクトル。`pnt`はサイズ3のベクトルである必要があります。定数。
  * **`vec::Vector{Float64}`** -> 可変サイズのベクトル。`vec`はベクトルであり、行列ではありません。`vec`はサイズ3*nrayである必要があります。定数。
  * **`geomgroup::Vector{UInt8}`** -> **オプション**のサイズ6のベクトル。`geomgroup`はサイズ6のベクトルである必要があります。必要ない場合は`nothing`に設定できます。定数。
  * **`flg_static::UInt8`**
  * **`bodyexclude::Int32`**
  * **`geomid::Vector{Int32}`** -> 可変サイズのベクトル。`geomid`はベクトルであり、行列ではありません。distと`geomid`はサイズnrayである必要があります。
  * **`dist::Vector{Float64}`** -> 可変サイズのベクトル。`dist`はベクトルであり、行列ではありません。`dist`とgeomidはサイズnrayである必要があります。
  * **`nray::Int32`**
  * **`cutoff::Float64`**
