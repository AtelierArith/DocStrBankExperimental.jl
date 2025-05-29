```
weight_repr(cal::MultipleCalibration)
weight_repr(weight::Number)
```

`cal.weight` または `weight` の文字列表現を返します。

0 の場合は "none"、-0.5 の場合は "1/√x"、-1 の場合は "1/x"、-2 の場合は "1/x²"、他の正の `weight` の場合は "x^`$weight`"、他の負の `weight` の場合は "1/x^`$(abs(weight))`" です。
