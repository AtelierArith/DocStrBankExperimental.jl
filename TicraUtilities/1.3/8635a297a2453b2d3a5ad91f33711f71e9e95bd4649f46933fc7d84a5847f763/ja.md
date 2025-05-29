```
get_srr(tep::TEP)
```

後方入射の反射配列を返します。配列のサイズは、`TEPscatter`オブジェクトの場合は `(2, 2, length(theta), length(phi))` であり、`TEPperiodic`オブジェクトの場合は `(2, 2, length(theta), length(phi), length(freqs))` です。
