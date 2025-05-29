```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  M::ZZMatrix;
  check::Bool=true,
) -> TorQuadModuleMap
```

2つのトーション二次モジュール `T` と `S`、および `M` という行列が与えられたとき、`T` と `S` の基礎となる群の間のアーベル群準同型を定義する行列 `M` に基づいて、対応するアーベル群準同型を返します。`check` が `true` に設定されている場合、この関数は `M` が `T` と `S` の間の有限アーベル群の準同型を定義しているかどうかをチェックします。
