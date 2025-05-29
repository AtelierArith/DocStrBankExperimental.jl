```
m, ω = ncfmargin(P, K)
```

正規化された互いに素な因子マージンは、*逆数*として定義されます

$$
\begin{Vmatrix}
\begin{bmatrix}
I \\ K
\end{bmatrix} (I + PK)^{-1} \begin{bmatrix}
I & P
\end{bmatrix}
\end{Vmatrix}_\infty
$$

マージンが≥ 0.25-0.3は、ロバスト性にとって妥当です。

コントローラ `K` がマージン `m` で `P` を安定化させる場合、`nugap(P, P̃) < m` であれば `K` は `P̃` も安定化させます。

さらに [`extended_gangoffour`](@ref)、[`diskmargin`](@ref)、[`controller_reduction_plot`](@ref) を参照してください。

# 拡張ヘルプ

  * 互いに素な因子の不確実性に対するロバスト性は、入力の不確実性に対するロバスト性を必ずしも意味しません。Skogestad p. 96 注記 4

```
