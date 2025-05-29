```
evaluate_integral(f::UnivariateFunction,left::Real, right::Real)
evaluate_integral(f::UnivariateFunction,left::Union{Date,DateTime}, right::Union{Date,DateTime})
```

これは、関数の積分を左限界から右限界まで計算し、スカラーを返します。

`Date`、`DateTime`が入力されると、最初に`years_from_global_base`関数を使用してスカラーに変換されます。

### 入力

  * `f` - `UnivariateFunction`。
  * `left` - 左限界（スカラー）
  * `right` - 右限界（スカラー）

### 返り値

  * `Real`。
