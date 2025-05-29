```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  img::Vector;
  check::Bool=true
) -> TorQuadModuleMap
```

2つのトーション二次モジュール `T` と `S` が与えられ、`S` の要素のリスト `img` が `ngens(T)` と同じ数の要素を含む場合、`T` の生成元を `img` の要素に対応させるアーベル群準同型を返します。`check` が `true` に設定されている場合、関数は入力が有限アーベル群の準同型を定義するかどうかをチェックします。
