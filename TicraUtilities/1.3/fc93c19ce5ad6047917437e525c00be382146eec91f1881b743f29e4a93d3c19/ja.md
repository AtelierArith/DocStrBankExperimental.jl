```
get_sfr(tep::TEP)
```

後方入射のための伝送配列を返します。配列のサイズは、`TEPscatter`オブジェクトの場合は `(2, 2, length(theta), length(phi))` であり、`TEPperiodic`オブジェクトの場合は `(2, 2, length(theta), length(phi), length(freqs))` です。
