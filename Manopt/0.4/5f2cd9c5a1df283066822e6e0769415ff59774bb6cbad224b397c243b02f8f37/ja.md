```
HestenesStiefelCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$、および勾配が含まれ、最後の更新方向は $\delta=\delta_k$ です。これは、[HestenesStiefel:1952](@cite) を多様体に適応させたものです。

$$
\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k
$$

とします。すると、更新は次のようになります。

$$
β_k = \frac{\langle X_{k+1}, \nu_k \rangle_{p_{k+1}} }
    { \langle P_{p_{k+1}\gets p_k} \delta_k, \nu_k\rangle_{p_{k+1}} },
$$

ここで、$P_{a\gets b}(⋅)$ は点 $a$ から $b$ への接空間のベクトル輸送を示します。

# コンストラクタ

```
function HestenesStiefelCoefficient(transport_method::AbstractVectorTransportMethod)
function HestenesStiefelCoefficient(M::AbstractManifold = DefaultManifold(2))
```

平行輸送がデフォルトのベクトル輸送であり、新しいストレージがデフォルトで作成される Hestenes Stiefel 係数更新ルールを構築します。

さらに [`conjugate_gradient_descent`](@ref) を参照してください。
