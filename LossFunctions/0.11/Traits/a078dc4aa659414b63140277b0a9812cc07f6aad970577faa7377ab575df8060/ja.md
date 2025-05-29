```
deriv(loss, output, target) -> Number
```

`loss`関数に対する`output`の解析的導関数を計算します。`target`と`output`は異なる数値型である可能性があるため、その場合は与えられた損失に適した方法で昇格が行われます。
