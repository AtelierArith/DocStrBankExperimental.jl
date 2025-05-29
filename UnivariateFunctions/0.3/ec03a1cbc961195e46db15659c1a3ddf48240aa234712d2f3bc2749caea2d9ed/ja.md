```
left_integral(f::UnivariateFunction, right::Real)
left_integral(f::UnivariateFunction, right::Union{Date,DateTime})
```

これは、関数の右限界からの積分を計算し、それをUnivariateFunctionとして返します。したがって、この積分関数を点xで評価すると、rightとxの間の積分が得られます。

`Date`または`DateTime`が入力されると、最初に`years_from_global_base`関数を使用してスカラーに変換されます。

### 入力

  * `f` - `UnivariateFunction`。
  * `right` - 右限界（スカラー）

### 返り値

  * `UnivariateFunction`。
