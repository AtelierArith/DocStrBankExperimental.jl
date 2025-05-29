```
rmeye(
    n::Integer;
    backend::Backend = CPU(),
    float_type::Type{Tv} = Float32,
    int_type::Type{Ti} = Int)::RefinementMatrix{Tv, Ti} where {Tv, Ti <: Integer}
```

単位リファインメント行列を構築します。

## 入力

  * `n`: 単位行列のサイズは n×n です
  * `backend`: 行列データの KernelAbstractions バックエンド
  * `float_type`: 行列データの値の型
  * `int_type`: 行列データの整数型
