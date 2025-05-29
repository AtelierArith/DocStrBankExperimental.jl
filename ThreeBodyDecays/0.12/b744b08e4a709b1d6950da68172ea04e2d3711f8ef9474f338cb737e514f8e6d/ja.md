```
phase_space_integrand(function_σs, ms; k::Int)
```

与えられた関数 `function_σs` と質量タプル `ms` のための相空間積分因子を計算します。重要な引数 `k` はマッピングを指定します: `σk->[0,1]`, zk->[0,1]。これは、数値積分器に渡すための x に関する積分因子関数を返します。x ∈ [0,1]x[0,1] の範囲です。

# 引数

  * `function_σs`: マンデルスタムタプルを受け取りスカラーを返す関数。
  * `ms`: 質量を表すスカラー。
  * `k`: マッピングインデックスを表す整数。

# 使用法

```julia
integrand = phase_space_integrand(function_σs, ms; k)
```

# 参照

  * `x2σs`
  * `projection_integrand`
