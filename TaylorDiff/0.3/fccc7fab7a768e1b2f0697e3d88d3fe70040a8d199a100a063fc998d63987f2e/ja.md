```
TaylorScalar{T, P}
```

テイラー多項式の表現。

# フィールド

  * `value::T`: ゼロ次係数
  * `partials::NTuple{P, T}`: i 番目の要素は i 番目の導関数を格納します。
