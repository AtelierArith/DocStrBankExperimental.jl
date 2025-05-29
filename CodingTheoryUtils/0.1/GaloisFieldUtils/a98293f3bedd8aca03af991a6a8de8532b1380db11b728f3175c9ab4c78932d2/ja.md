```
num_terms(f::Polynomial{F}) where F <: AbstractGaloisField -> Int
```

多項式 `f` の非ゼロ項（係数）の数を返します。

# 引数

  * `f::Polynomial{F}`: 入力多項式。

# 戻り値

  * `Int`: 非ゼロ係数の数。

# 例

julia> p = Polynomial([F2(1), F2(1), F2(0), F2(1)]); # 1 + x + x^3

julia> num_terms(p) 3 ```
