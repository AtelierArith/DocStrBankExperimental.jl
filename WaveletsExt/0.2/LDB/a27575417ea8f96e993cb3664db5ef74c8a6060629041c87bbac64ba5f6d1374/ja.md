```
fit_transform(f, X, y)
```

信号 `X` とラベル `y` を LDB クラス `f` に基づいてフィットおよび変換します。この関数は本質的に `fit!` と `transform` の両方を1つにまとめたもので、トレーニングデータセットの LDB コエフィシエントを抽出する際に推奨されるメソッドです。テストデータセットの場合、最初にトレーニングデータセットで `fit!` を実行し、その後テストデータセットで `transform` を実行する必要があります。

# 引数

  * `f::LocalDiscriminantBasis`: ローカル判別基底オブジェクト。
  * `Xw::AbstractArray{S} where S<:AbstractFloat`: 同じサイズの分解された信号のグループで、3次元（1D信号）または4次元（2D信号）に配置されています。
  * `y::AbstractVector{T} where T`: X の各信号に対応するラベル。

# 戻り値

  * `Xc::Matrix{S}`: `X` から抽出された LDB 特徴の行列で、各列は対応する信号から抽出されたコエフィシエントに対応します。

# 例

```julia
using Wavelets, WaveletsExt

X, y = generateclassdata(ClassData(:tri, 5, 5, 5))
f = LocalDiscriminantBasis()
Xc = fit_transform(f, X, y)
```

**参照:** [`LocalDiscriminantBasis`](@ref), [`fit!`](@ref), [`transform`](@ref),     [`inverse_transform`](@ref), [`change_nfeatures`](@ref)
