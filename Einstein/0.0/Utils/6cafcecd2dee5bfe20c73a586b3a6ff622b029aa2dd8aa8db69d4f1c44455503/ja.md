```
barycentric_differentiation_matrix(x::AbstractVector{TF}, w::AbstractVector{TF}, k::Integer=1, t::Union{AbstractVector{TF},Nothing}=nothing) where {TF<:AbstractFloat}
```

バリセントリック微分行列を計算します。

# 引数

  * `x::AbstractVector{TF}` : 補間点のベクトル
  * `w::AbstractVector{TF}` : 補間点のバリセントリック重み
  * `k::Integer` : 微分の次数（デフォルト: 1）
  * `t::AbstractVector{TF}` : 角度のベクトル（デフォルト: nothing）

# 参考文献:

  * [chebfun/@chebcolloc/baryDiffMat.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc/baryDiffMat.m)
  * [Baltensperger2003](@citet*)
