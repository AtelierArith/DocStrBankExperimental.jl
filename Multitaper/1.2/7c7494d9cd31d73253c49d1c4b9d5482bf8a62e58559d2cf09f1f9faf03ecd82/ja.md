```
dpss_tapers(n,w,k,tap_or_egval)
```

単純に離散的な前向き球面波列のテーパーと固有値を計算します。

...

# 引数

  * `n::Int64`: テーパーの長さ
  * `nw::Float64`: 時間-帯域幅積
  * `k::Int64`: テーパーの数
  * `tap_or_egval::Symbol = :tap`: :tap、:egval、または :both のいずれか

...

...

# 出力

  * `vv::Vector{Float64}`: tap*or*egval が :tap に設定されている場合の固有値の行列
  * `dpss_eigval`: dpss テーパーを含む構造体

...
