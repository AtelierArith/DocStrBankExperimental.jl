```julia
abstract type AbstractFactorization{Tv, Ti}
```

ExtendableSparseMatrixを持つ因数分解のための抽象型。

そのような前処理器は、次のフィールドを持つ必要があります。

```
  A::ExtendableSparseMatrix
  fact
  phash::UInt64
```

そして、次のメソッドを提供する必要があります。

```
  update!(precon)
```

アイデアは、行列のパターンが変更されたかどうかに応じて、前処理器を更新するために異なるステップが必要であるということです。

さらに、彼らはフィールドとしてExtendableSparseMatrix `A`を持ち、構築後の一貫性を保証する`update!`メソッドを持っています。
