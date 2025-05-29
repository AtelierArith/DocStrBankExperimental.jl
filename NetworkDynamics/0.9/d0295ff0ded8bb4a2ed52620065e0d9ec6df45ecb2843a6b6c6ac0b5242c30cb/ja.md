```
set_defaults!(nw::Network, s::NWState)
```

与えられた状態の値にネットワークのデフォルト値を設定します。見つかった固定点をネットワークメタデータに「保存」するために使用できます。

`missing`、`nothing`、または`NaN`の値は無視されます。
