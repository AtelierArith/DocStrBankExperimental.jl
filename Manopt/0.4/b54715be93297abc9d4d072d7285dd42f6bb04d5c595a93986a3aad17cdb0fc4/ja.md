```
FletcherReevesCoefficient <: DirectionUpdateRule
```

共役勾配法の更新係数を計算します。ここで、[`ConjugateGradientDescentState`](@ref)`cgds` には、最後の反復 $p_k,X_k$、現在の反復 $p_{k+1},X_{k+1}$ の反復と勾配がそれぞれ含まれ、最後の更新方向 $\delta=\delta_k$ は、[FletcherReeves:1964](@cite) に基づいて多様体に適応されています：

$$
β_k =
\frac{\lVert X_{k+1}\rVert_{p_{k+1}}^2}{\lVert X_k\rVert_{x_{k}}^2}.
$$

また、[`conjugate_gradient_descent`](@ref) も参照してください。

# コンストラクタ

```
FletcherReevesCoefficient(a::StoreStateAction=())
```

Fletcher—Reeves 係数更新ルールを構築します。デフォルトでは新しいストレージが作成されます。
