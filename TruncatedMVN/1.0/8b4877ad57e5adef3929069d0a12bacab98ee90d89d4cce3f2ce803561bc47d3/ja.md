```
 TruncatedMVNormal(mu::T, cov::S, lb::T, ub::T) where {T<:AbstractVector{<:AbstractFloat},S<:AbstractArray{<:AbstractFloat}}
```

[`TruncatedMVN.TruncatedMVNormal`](@ref) 分布の内部コンストラクタです。

[`TruncatedMVN.sample`](@ref) を使用して正確にサンプリングできるトランケート多変量正規分布を生成します。

# 引数

  * `mu::T`: D次元の平均ベクトル。
  * `cov::S`: DxD次元の共分散行列。
  * `lb::T`: D次元の下限ベクトル。
  * `ub::T`: D次元の上限ベクトル。

境界は `-Inf`/`Inf` である可能性があります。
