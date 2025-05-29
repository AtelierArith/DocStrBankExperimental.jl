```
TaylorArray{T, N, A, P}
```

配列モードでのテイラー多項式の表現。

# フィールド

  * `value::A`: ゼロ次係数
  * `partials::NTuple{P, A}`: i 番目の要素は i 番目の導関数を格納します。
