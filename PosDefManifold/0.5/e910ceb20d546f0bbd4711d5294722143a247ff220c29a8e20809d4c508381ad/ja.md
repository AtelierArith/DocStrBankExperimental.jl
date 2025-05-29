```julia
    vecP(S::Union{ℍ{T}, Symmetric{R}};
         range::UnitRange=1:size(S, 2)) where T<:RealOrComplex where R<:Real =
```

*接ベクトル化* 接ベクトル（`Hermitian` または `Symmetric` 行列）$S$:  mat ↦ vec.

対角要素には重み $1$ を、非対角要素には重み $√2$ を与え、ノルムを保持します（Barachant et *al.*, 201E)[🎓](@ref)、例えば

$$
∥S∥_F=∥vecP(S)∥_F
$$

.

結果は $n(n+1)/2$ 要素を持つベクトルで、ここで $n$ は $S$ のサイズです。

$$
S
$$

は `Hermitian` または `Symmetric` としてフラグ付けされている必要があります。詳細は [行列の型変換](@ref) を参照してください。

逆操作は [`matP`](@ref) によって提供され、常に `Hermitian` 行列を返します。

オプションのキーワード引数 `range` が提供されると、ベクトル化は範囲内の行（または列、入力行列が対称またはエルミートであるため）にのみ関係します。この場合、操作は [`matP`](@ref) によって元に戻すことはできません。つまり、この場合、行列は接空間に「固定」されます。

**例**

```julia
using PosDefManifold
P=randP(3)
Q=randP(3)
G=mean(Fisher, P, Q)
# PをPとQの幾何平均によって与えられた基点で投影
S=logMap(Fisher, P, G)
# Sをベクトル化
v=vecP(S)
# Sの最初の2列のみをベクトル化
v=vecP(S; range=1:2)
```
