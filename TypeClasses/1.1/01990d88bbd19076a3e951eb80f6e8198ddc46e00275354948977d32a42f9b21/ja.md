```
orelse(a, b)  # overload this
⊘(a, b)  # alias \oslash
orelse(a, b, c, d, ...)  # using orelse(a, b) internally
```

代替の論理を実装します。これは、2つの選択肢 a と b があり、最初の有効なものを取るというものです。「alternatives」ではなく「orelse」を選んだのは、選択における内在的な非対称性を強調するためです。

演算子 ⊘ (\oslash) は、\oplus に似た中置演算子を持つために選ばれましたが、明確に区別可能で非対称であり、ある意味で選択の意味を捉えています。スラッシュは実際に選択を示すために使用されます（少なくともドイツ語のような言語では）、幸運なことに \oslash は存在し（\odiv とは呼ばれません）。
