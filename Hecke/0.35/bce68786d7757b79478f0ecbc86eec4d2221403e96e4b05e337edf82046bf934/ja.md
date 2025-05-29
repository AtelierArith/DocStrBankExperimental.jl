```
normal_form(T::TorQuadModule; partial=false) -> TorQuadModule, TorQuadModuleMap
```

与えられたトーション二次モジュール `T` の正規形 `N` と射影 `T -> N` を返します。

`K` を `T` の二次形式の根とします。すると `N = T/K` は半正則です。二つの半正則トーション二次モジュールは、正規形が等しい場合に限り等距離です。
