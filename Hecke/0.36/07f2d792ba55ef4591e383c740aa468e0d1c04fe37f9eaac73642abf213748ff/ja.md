```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  A::Vector,
  B::Vector;
  check::Bool=true,
) -> TorQuadModuleMap
```

2つのトーション二次モジュール `T` と `S`、およびそれぞれ `T` と `S` の要素のリスト `A` と `B` が与えられたとき、すべての i に対して `A[i]` を `B[i]` にマッピングする `T` と `S` の間のアーベル群準同型を返します。`check` が `true` に設定されている場合、関数は入力が有限アーベル群の準同型を定義するかどうかをチェックします。
