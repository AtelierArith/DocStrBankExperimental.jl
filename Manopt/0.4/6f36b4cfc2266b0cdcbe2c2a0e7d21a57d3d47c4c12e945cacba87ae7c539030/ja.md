```
LiuStoreyCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$、および勾配が含まれ、最後の更新方向は $\delta=\delta_k$ です。これは、[LiuStorey:1991](@cite) を多様体に適応させたものです。

$$
\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k
$$

とします。ここで、$P_{a\gets b}(⋅)$ は、点 $a$ での接空間から点 $b$ へのベクトル輸送を示します。

係数は次のように表されます。

$$
β_k = -
\frac{ \langle X_{k+1},\nu_k \rangle_{p_{k+1}} }
{\langle \delta_k,X_k \rangle_{p_k}}.
$$

また、[`conjugate_gradient_descent`](@ref) も参照してください。

# コンストラクタ

```
function LiuStoreyCoefficient(t::AbstractVectorTransportMethod)
function LiuStoreyCoefficient(M::AbstractManifold = DefaultManifold(2))
```

Lui Storey 係数更新ルールを構築します。ここで、平行輸送はデフォルトのベクトル輸送であり、新しいストレージがデフォルトで作成されます。
