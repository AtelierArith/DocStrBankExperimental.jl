```
evaluate!(spline_dimension)
```

サンプルポイントごとに、非ゼロ値を持つ`spline_dimension.degree + 1`基底関数の値を取得します。これはCox-de Boor再帰式に基づいています。

l番目のサンプルポイント`t`はサンプルインデックス`i`を持ち、つまり`t ∈ [tᵢ, tᵢ₊₁)`です。したがって、`Bᵢ₀(t) = 1, Bⱼ₀(t) = 0 for j ≠ i`です。次数`k`の場合、`t`は`Bⱼₖ`の定義域にあり、これは`[tⱼ, tⱼ₊ₖ₊₁)`です。ここで、`j = i - k, ..., i`です。

## 引数

  * `spline_dimension`
