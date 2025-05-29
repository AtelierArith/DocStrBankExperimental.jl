```
orthonormal([T,] D, k) -> ws
```

`k`列を持つ行列`ws`を返します。各列は`D`次元の直交正規ベクトルです。

`T`は戻り値の型で、`SMatrix`または`Matrix`のいずれかです。指定されていない場合、`D*k < 100`なら`SMatrix`、それ以外の場合は`Matrix`になります。
