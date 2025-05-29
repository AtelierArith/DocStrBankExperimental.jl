```
right_integral(f::UnivariateFunction, left::Real)
right_integral(f::UnivariateFunction, left::Union{Date,DateTime})
```

これは関数の左限からの積分を計算し、それをUnivariateFunctionとして返します。したがって、この積分関数を点xで評価すると、leftとxの間の積分が得られます。

`Date`または`DateTime`が入力されると、最初に`years_from_global_base`関数を使用してスカラーに変換されます。

### 入力

  * `f` - `UnivariateFunction`。
  * `left` - 左限（スカラー）

### 返り値

  * `UnivariateFunction`。
