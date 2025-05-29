```
mdslepian(w, k, t)
```

1D 欠損データ問題のための一般化されたプロレート球面系列

...

# 引数

## 位置引数

  * `w::Float64`: 帯域幅
  * `k::Int64`: スレピアンテーパーの数、2*bw*length(x) 以下でなければならない
  * `t::Vector{Int64}`: 時間インデックスを含むベクター

...

...

# 出力

  * `lambda,u::Tuple{Vector{Float64}, Vector{Float64}}`: 集中度とテーパーを含むタプル

...

参照: [`mdmultispec`](@ref), [`gpss`](@ref)
