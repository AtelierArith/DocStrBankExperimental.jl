二次関数の基礎データを表す構造体。主にコスト関数 `f(x) = quadratic_term*x^2 + proportional_term*x + constant_term` の表現に使用されます。

# 引数

  * `quadratic_term::Float64`: 表現される関数の二次項
  * `proportional_term::Float64`: 表現される関数の比例項
  * `constant_term::Float64`: 表現される関数の定数項
