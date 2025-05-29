```
HagerZhangCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$ の反復と勾配が含まれ、最後の更新方向 $\delta=\delta_k$ は [HagerZhang:2005](@cite) に基づいています。多様体に適応させると、$\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k$ となります。ここで、$P_{a\gets b}(⋅)$ は点 $a$ から $b$ への接空間のベクトル輸送を示します。

$$
β_k = \Bigl\langle\nu_k -
\frac{ 2\lVert \nu_k\rVert_{p_{k+1}}^2 }{ \langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}} }
P_{p_{k+1}\gets p_k}\delta_k,
\frac{X_{k+1}}{ \langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}} }
\Bigr\rangle_{p_{k+1}}.
$$

この方法には、著者たちによって提案された数値的安定性が含まれています。

また、[`conjugate_gradient_descent`](@ref) も参照してください。

# コンストラクタ

```
function HagerZhangCoefficient(t::AbstractVectorTransportMethod)
function HagerZhangCoefficient(M::AbstractManifold = DefaultManifold(2))
```

Hager Zhang 係数更新ルールを構築します。ここで、平行輸送はデフォルトのベクトル輸送であり、新しいストレージはデフォルトで作成されます。
