```
remove_padding(m, nb; true_adjoint=False)
```

配列 `m` からパディングを削除します。これは [`pad_array`](@ref) の随伴です。

パラメータ

  * `m`: パディングを削除する配列。
  * `nb`: パディングのサイズ。次元ごとに1つの (nb*left, nb*right) タプルを持つタプルの配列。
  * `true_adjoint`: アンパディングモード、デフォルトは False。`true_adjoint=true` の場合、パディングをエッジポイントに合計します。

これは随伴テストの目的でのみこの方法で使用する必要があります。
