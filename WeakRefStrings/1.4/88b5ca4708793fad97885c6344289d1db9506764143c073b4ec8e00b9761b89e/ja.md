```
PosLenString(buf::Vector{UInt8}, poslen::PosLen, e::UInt8)
```

バイトバッファ（`buf`）、`poslen`、および `e` エスケープ文字を受け取るカスタム文字列表現であり、`buf` の領域を文字列として遅延的に扱うことを可能にします。これは、`PosLen` の配列（インライン）を単一の `buf` と `e` と共に格納し、個々の要素をインデックスする際に `PosLenString` を返す [`PosLenStringVector`](@ref) の一部として最も効率的に使用できます。
