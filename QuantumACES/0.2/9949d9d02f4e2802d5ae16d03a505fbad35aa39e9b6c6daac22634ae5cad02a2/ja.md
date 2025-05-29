```
get_wht_transform(d::Design, est_type::Symbol; inverse::Bool = false)
```

パディングされたゲートエラー確率をパディングされたゲート固有値にマッピングする変換行列を返します。`inverse`が`true`の場合は逆変換を返します。この行列の型は推定器のタイプ`est_type`（`:ordinary`、`:marginal`、または`:relative`）に依存し、設計`d`のゲートデータを使用して計算されます。
