```
transform(f, X)
```

信号 `X` から、以前に適合した信号に基づいて構築された LDB ツリーに基づいて LDB 特徴を抽出します。

# 引数

  * `f::LocalDiscriminantBasis`: ローカル判別基底オブジェクト。
  * `X::AbstractArray{S} where S<:AbstractFloat`: 同じサイズの信号のグループで、2次元（1D 信号）または 3次元（2D 信号）の次元に配置されています。

# 戻り値

  * `Xc::Matrix{S}`: `X` から抽出された LDB 特徴の行列で、各列は対応する信号から抽出された係数に対応します。

# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
fit!(f, X, y)
Xc = transform(f, X)
```

**関連情報:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
