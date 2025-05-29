```
nearestPosDef(X::Union{𝔻, 𝕄}; tol::Real=0.)
```

対角行列または任意の正方行列 `X` の最近接対称/Hermitian 正半定値行列をフロベニウスノルムに従って返します。 `X` の対称部分の固有値がすべて非負である場合、結果は正定値であり、`Hermitian` としてフラグ付けされます。そうでない場合は正半定値であり、フラグ付けされません。最近接行列は次のように与えられます。

$$
(Y+H)/2
$$

ここで

$$
Y=(X+X^H)/2
$$

は `X` の対称部分であり、$H$ は $Y$ の対称極因子です。詳細および計算方法については Higham(1988)[🎓](@ref) を参照してください。

**関連情報**: [`det1`](@ref), [`procrustes`](@ref).

**例**

```julia
using LinearAlgebra, PosDefManifold
X=randn(5, 5) # 任意の5x5行列を生成
S=nearestPosDef(X)

P=randP(5) # ランダムな実正定値5x5行列を生成
S=nearestPosDef(Matrix(P)) # Hermitian行列を`Matrix`として型変換
# Pが正定値行列であるため、SはPと等しいはずです
S ≈ P ? println(" ⭐ ") : println(" ⛔ ")
```
