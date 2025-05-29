```
`build_blp_model(m::JuMP.Model, bp::BilevelLP, x, y; [comp_method])`
```

既存のJuMPモデルに下位レベルの制約と最適性条件を追加します。これは、上位レベルの実行可能性制約と目的がすでに設定されていることを前提としています。

タプル `(m, x, y, λ, s)` を返します。

補完制約を処理するためにオプションのキーワード `comp_method` を渡すことができ、デフォルトは `SOS1Complementarity` です。
