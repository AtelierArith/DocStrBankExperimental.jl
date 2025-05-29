```julia
abstract type AbstractFactorization
```

ExtandableSparseMatrixを持つ因数分解のための抽象型。

この型は「型柔軟」（行列要素型に関して）であり、遅延構築可能（行列を知らなくても構築でき、後で更新可能）なLU因数分解または前処理器を意図しています。これは、通常の`ldiv!`メソッドを提供する異なる具体的な型固定因数分解をラップします。

任意の前処理器/因数分解`MyFact`は、以下のフィールドを持つべきです。

```
  A::ExtendableSparseMatrix
  factorization
  phash::UInt64
```

そして、以下のメソッドを提供するべきです。

```
  MyFact(;kwargs...) 
  update!(precon::MyFact)
```

アイデアは、行列パターンが変更されたかどうかに応じて、前処理器を更新するために異なるステップが必要であるということです。
