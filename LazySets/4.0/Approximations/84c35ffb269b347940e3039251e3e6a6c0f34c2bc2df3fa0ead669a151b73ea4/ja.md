```
overapproximate(lm::LinearMap{N, <:AbstractZonotope, NM,
                              <:AbstractIntervalMatrix{NM}},
                ::Type{<:Zonotope}) where {N, NM}
```

ゾノトープ集合の区間行列線形写像をゾノトープで過大評価します。

### 入力

  * `lm`       – ゾノトープ集合の区間行列線形写像
  * `Zonotope` – 目標集合の型

### 出力

線形写像を過大評価するゾノトープ。

### アルゴリズム

この実装は、[AlthoffSB07](@citet)で提案された方法を使用します。

区間行列 $M = \tilde{M} + ⟨-\hat{M},\hat{M}⟩$（従来の行列と対称区間行列に分割）とゾノトープ $⟨c, g_1, …, g_m⟩$ が与えられたとき、結果のゾノトープ $⟨\tilde{M}c, \tilde{M}g_1, …, \tilde{M}g_m, v_1, …, v_n⟩$ を計算します。ここで、$v_j$, $j = 1, …, n$ は次のように定義されます。

$$
    v_j = \begin{cases} 0 & i ≠ j \\
          \hat{M}_j (|c| + ∑_{k=1}^m |g_k|) & i = j. \end{cases}
$$
