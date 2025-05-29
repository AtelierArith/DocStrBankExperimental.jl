```
hom(
  T::TorQuadModule,
  S::TorQuadModule,
  img::Vector;
  check::Bool=true
) -> TorQuadModuleMap
```

2つのトーション二次モジュール `T` と `S` と、`S` の要素のリスト `img` を与えられ、`ngens(T)` と同じ数の要素を含む場合、`T` の生成元を `img` の要素にマッピングする `T` と `S` の間のアーベル群準同型を返します。`check` が `true` に設定されている場合、関数は入力が有限アーベル群の準同型を定義するかどうかをチェックします。
