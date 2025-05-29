```
projection_integrand(function_σs, ms, σk; k)
```

与えられた関数 `function_σs`、質量タプル `ms`、およびマンデルスタム変数 `σk` のための射影積分関数を計算します。`k` はキーワード引数で指定されます。これは、数値積分器に渡すための x の積分関数を返します。x ∈ [0,1]。

# 引数

  * `function_σs`: マンデルスタムタプルを受け取り、スカラーを返す関数。
  * `ms`: 質量を表すスカラー。
  * `σk`: マンデルスタム変数を表すスカラー。
  * `k`: 運動量移動を表すスカラー（オプション）。

# 使用法

```julia
plot(4.2, 4.6) do e1
	I = Base.Fix1(unpolarized_intensity, model)
	integrand = projection_integrand(I, masses(model), e1^2; k = 3)
	e1 * quadgk(integrand, 0, 1)[1]
end
```
