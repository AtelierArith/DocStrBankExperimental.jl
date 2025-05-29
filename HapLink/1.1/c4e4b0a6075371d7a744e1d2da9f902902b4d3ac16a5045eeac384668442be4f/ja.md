```
relativepos(v::Variation, r::Union{SAM.Record,BAM.Record})
```

`v`の`r`内のシーケンスにおける相対位置を計算します。`v`が`r`の範囲外の場合、`r`の前の位置には`0`、`r`の後の位置には`1`を返します。
