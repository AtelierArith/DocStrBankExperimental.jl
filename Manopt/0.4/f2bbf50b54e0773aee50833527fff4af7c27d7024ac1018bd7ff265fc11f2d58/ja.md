```
PolakRibiereCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$、および勾配が含まれ、最後の更新方向 $\delta=\delta_k$ は、[PolakRibiere:1969](@cite) および [Polyak:1969](@cite) に基づいて、マニフォールドに適応されています。

$$
\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k
$$

とします。ここで、$P_{a\gets b}(⋅)$ は、点 $a$ から $b$ への接空間のベクトル輸送を示します。

次に、更新は次のように表されます。

$$
β_k =
\frac{ \langle X_{k+1}, \nu_k \rangle_{p_{k+1}} }
{\lVert X_k \rVert_{p_k}^2 }.
$$

# コンストラクタ

```
function PolakRibiereCoefficient(
    M::AbstractManifold=DefaultManifold(2);
    t::AbstractVectorTransportMethod=default_vector_transport_method(M)
)
```

PolakRibiere係数更新ルールを構築します。ここで、平行輸送はデフォルトのベクトル輸送であり、新しいストレージはデフォルトで作成されます。

さらに [`conjugate_gradient_descent`](@ref) を参照してください。
