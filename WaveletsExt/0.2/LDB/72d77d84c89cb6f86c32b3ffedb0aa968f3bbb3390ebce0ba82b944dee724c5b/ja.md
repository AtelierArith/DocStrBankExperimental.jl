```
fit!(f, X, y)
```

ローカル判別基底特徴選択アルゴリズム `f` を信号 `X` にラベル `y` で適合させます。

# 引数

  * `f::LocalDiscriminantBasis`: ローカル判別基底オブジェクト。
  * `X::AbstractArray{S} where S<:AbstractFloat`: 同じサイズの信号のグループで、2次元（1D信号）または3次元（2D信号）に配置されています。
  * `y::AbstractVector{T} where T`: X内の各信号に対応するラベル。

# 戻り値

  * `f::LocalDiscriminantBasis`: フィールドが更新された同じLDBオブジェクト `f`。

# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
fit!(f, X, y)
```

**関連情報:** [`LocalDiscriminantBasis`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
