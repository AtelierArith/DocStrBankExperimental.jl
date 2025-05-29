```
remove_column!(C::UpdatableCholesky, i::Int)
```

`UpdatableCholesky`因子分解`C`を更新し、元の行列の`i`行目と列を削除します。複雑さは`O(n²)`です。
