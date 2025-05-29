```
`build_blp_model(bp::BilevelLP, solver; [comp_method])`
```

bpからのデータに基づいて、ソルバーを使用してJuMPモデル（制約と目的）を構築します。

タプル `(m, x, y, λ, s)` を返します。

補完制約を処理するためにオプションのキーワード `comp_method` を渡すことができ、デフォルトは `SOS1Complementarity` です。
