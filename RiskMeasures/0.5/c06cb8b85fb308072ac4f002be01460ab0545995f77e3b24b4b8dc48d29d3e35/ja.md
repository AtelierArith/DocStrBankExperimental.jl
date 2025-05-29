```
CVaR(x̃, α)
```

確率変数 `x̃` のレベル `α` における条件付きバリューアットリスクを計算します。

```
CVaR(values, pmf, α; ...)
```

確率質量関数 `pmf` と `values` を持つ離散確率変数の CVaR を計算します。

リスクレベル `α` は $α ∈ [0,1]$ を満たさなければなりません。リスク回避は `α` の増加に伴って減少し、`α = 1` は期待値を表し、`α = 0` は本質的下限（正の確率を持つ最小値）を計算します。

報酬最大化の設定を仮定し、双対形式を解きます。

$$
\min_{q ∈ \mathcal{Q}} q^T x̃
$$

ここで

$$
\mathcal{Q} = \left\{q ∈ Δ^n : q_i ≤ \frac{p_i}{α}\right\}
$$

$$
Δ^n
$$

は確率単体であり、$p$ は `x̃` の分布です。

# 戻り値

CVaR `value` とそれを達成する `pmf` を持つ名前付きタプル。

# キーワード引数:

  * `check_inputs=true`: 入力が有効であることを確認します。
  * `fast=false`: 線形時間の実験的実装を使用します。

詳細については: [https://en.wikipedia.org/wiki/Expected_shortfall](https://en.wikipedia.org/wiki/Expected_shortfall)
