```julia
unitary_matrices(ed::KeldyshED.EDCore) -> Vector

```

与えられた厳密対角化オブジェクト `ed` に保存されているすべての不変部分空間からユニタリ変換行列 $\hat U$ を収集します。
