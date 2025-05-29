```
DaiYuanCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$ および勾配が含まれ、最後の更新方向は $\delta=\delta_k$ です。これは、[DaiYuan:1999](@cite) を多様体に適応させたものです。

$$
\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k
$$

とします。ここで、$P_{a\gets b}(⋅)$ は点 $a$ から $b$ への接空間のベクトル輸送を示します。

係数は次のように表されます。

$$
β_k =
\frac{ \lVert X_{k+1} \rVert_{p_{k+1}}^2 }
{\langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}}}.
$$

また、[`conjugate_gradient_descent`](@ref) も参照してください。

# コンストラクタ

```
function DaiYuanCoefficient(
    M::AbstractManifold=DefaultManifold(2);
    t::AbstractVectorTransportMethod=default_vector_transport_method(M)
)
```

Dai—Yuan 係数更新ルールを構築します。ここで、平行輸送はデフォルトのベクトル輸送であり、新しいストレージがデフォルトで作成されます。
