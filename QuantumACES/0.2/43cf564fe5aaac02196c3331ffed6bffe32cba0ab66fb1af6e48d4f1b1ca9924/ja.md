```
get_wht_transform(gate_data::GateData; inverse::Bool = false)
```

パディングされたゲートエラー確率をパディングされたゲート固有値にマッピングする変換行列を返します。`inverse`が`true`の場合は逆変換を返し、ゲートデータ`gate_data`を使用して計算されます。
