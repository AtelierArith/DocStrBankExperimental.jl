```
maf_weights(x::SnpArray; max_weight::T = Inf)
```

マイナーアレル頻度に基づいて事前重みを計算します。

`w[i] = 1 / (2 * sqrt(p[i] (1 - p[i]))) ∈ (1, ∞)` という重みの配列を返します。ここで `p` は SnpArrays の `maf()` によって計算されたマイナーアレル頻度です。

  * `x`: SnpArray
  * `max_weight`: 任意の予測子の最大重み。デフォルトは `Inf` です。
