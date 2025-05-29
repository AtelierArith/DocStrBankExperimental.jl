```
ConjugateDescentCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$ および勾配が含まれ、最後の更新方向は $\delta=\delta_k$ です。これは、[Fletcher:1987](@cite) を多様体に適応させたものです：

$$
β_k =
\frac{ \lVert X_{k+1} \rVert_{p_{k+1}}^2 }
{\langle -\delta_k,X_k \rangle_{p_k}}.
$$

また、[`conjugate_gradient_descent`](@ref) も参照してください。

# コンストラクタ

```
ConjugateDescentCoefficient(a::StoreStateAction=())
```

共役降下係数更新ルールを構築します。デフォルトでは新しいストレージが作成されます。
