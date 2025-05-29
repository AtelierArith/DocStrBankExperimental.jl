```
AdditiveRungeKuttaMethod(rks)
AdditiveRungeKuttaMethod(As, bs, cs=map(A -> vec(sum(A, dims=2)), As))
```

加法ルンゲ・クッタ法を、バッチャー係数のコレクション `As`、`bs`、および `cs` で表現します。代わりに、コンストラクタに [`RungeKuttaMethod`](@ref)s のコレクションを渡すこともできます。`cs` が提供されていない場合、自律問題との整合性のために通常の「行和」要件が適用されます。

常微分方程式問題に適用される加法ルンゲ・クッタ法は

$$
  u'(t) = \sum_\nu f^\nu(t, u(t))
$$

の形を持ちます。

$$
\begin{aligned}
  y^i &= u^n + \Delta t \sum_\nu \sum_j a^\nu_{i,j} f^\nu(y^i), \\
  u^{n+1} &= u^n + \Delta t \sum_\nu \sum_i b^\nu_{i} f^\nu(y^i).
\end{aligned}
$$

特に、加法ルンゲ・クッタ法は、次のような分割問題に適用される分割RK法のスーパーセットです。

$$
  (u^1)'(t) = f^1(t, u^1, u^2),
  \quad
  (u^2)'(t) = f^2(t, u^1, u^2).
$$

# 参考文献

  * A. L. Araujo, A. Murua, and J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926-1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)
