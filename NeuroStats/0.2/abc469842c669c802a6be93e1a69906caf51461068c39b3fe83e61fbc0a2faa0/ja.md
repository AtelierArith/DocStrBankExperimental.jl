```
count_thresh(x; <keyword arguments>)
```

閾値を設定した要素を収集します。例えば、地形図において。

# 引数

  * `x::AbstractMatrix`
  * `t::Real`: 閾値
  * `t_type::Symbol=:g`: 閾値設定のルール：

      * `:eq`: =
      * `:geq`: ≥
      * `:leq`: ≤
      * `:g`: >
      * `:l`: <

# 戻り値

名前付きタプルを含みます：

  * `x_t::Matrix{Bool}`: 閾値設定された行列
  * `n::Int64`: 要素の数
