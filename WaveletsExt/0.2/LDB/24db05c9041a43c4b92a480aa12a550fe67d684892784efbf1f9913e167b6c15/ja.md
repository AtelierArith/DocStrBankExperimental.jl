```
fitdec!(f, Xw, y)
```

ローカル判別基底特徴選択アルゴリズム `f` を、分解された信号 `Xw` とラベル `y` に適合させます。

# 引数

  * `f::LocalDiscriminantBasis`: ローカル判別基底オブジェクト。
  * `Xw::AbstractArray{S} where S<:AbstractFloat`: 同じサイズの分解された信号のグループで、3次元（1D信号）または4次元（2D信号）に配置されています。
  * `y::AbstractVector{T} where T`: X内の各信号に対応するラベル。

# 戻り値

  * `f::LocalDiscriminantBasis`: フィールドが更新された同じLDBオブジェクト `f`。

# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
Xw = wpdall(X, f.wt)
fitdec!(f, Xw, y)
```

**関連情報:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`fit_transform`](@ref),     [`transform`](@ref), [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
