```
curve_fraction(f::Function,a::Real,b::Real,r::Real) -> Float64
```

曲線の長さの割合の位置を返します。区間 <`a`, `b`> から、曲線の長さはパラメータ関数 `f` によって与えられます。

# 引数

  * `f::Function`: 曲線の関数、
  * `a::Real`: 積分する区間の左端、
  * `b::Real`: 積分する区間の右端、
  * `r::Real`: 左から与えられた曲線の長さの割合、

# キーワード

# 返り値

  * `Float64`: 区間 <`a`, `b`> からの長さの割合の位置。

# 例外
