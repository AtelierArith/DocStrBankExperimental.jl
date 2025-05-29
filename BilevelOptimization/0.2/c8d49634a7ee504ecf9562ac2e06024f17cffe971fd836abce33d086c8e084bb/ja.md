```
`build_blp_model(m, B, d, x, y, s, F; [comp_method])`
```

データからすべてを `BilevelLP` にグループ化することなく、バイレベルJuMPモデルを構築します。補完制約を処理するためにオプションのキーワード `comp_method` を渡すことができ、デフォルトは `SOS1Complementarity` です。
