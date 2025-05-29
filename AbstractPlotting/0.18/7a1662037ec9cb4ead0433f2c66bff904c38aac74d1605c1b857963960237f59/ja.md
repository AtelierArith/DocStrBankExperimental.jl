```
convert_arguments(P, x, y, z)::Tuple{ClosedInterval, ClosedInterval, Matrix}
```

2つのClosedIntervals `x`、`y`とAbstractMatrix `z`を受け取り、閉じた範囲をlinspacesに変換します。サイズは `size(z, 1/2)` です。`P`はプロットタイプ（オプション）です。
