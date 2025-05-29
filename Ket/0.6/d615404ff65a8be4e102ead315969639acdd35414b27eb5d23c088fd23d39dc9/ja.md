```
tensor_probability(CG::Array, scenario::Tuple, behaviour::Bool = false)
```

マルチパーティベル関数 `CG` をコリンズ-ギシン表記から確率表記に変換します。`scenario` は入力と出力の数を詳細に示すタプルで、順序は (oa, ob, ..., ia, ib, ...) です。`behaviour` が `true` の場合は、代わりに振る舞いの変換を行います。正規化は仮定しません。
