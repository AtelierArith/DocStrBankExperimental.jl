```
hermitian_space(E::NumField, n::Int; cached::Bool = true) -> HermSpace
```

次の条件を満たすとき、`E` 上の次元 `n` のエルミート空間を作成します。グラム行列は単位行列に等しくなります。数体 `E` は二次拡張でなければならず、すなわち、$degree(E) == 2$ が成り立たなければなりません。
