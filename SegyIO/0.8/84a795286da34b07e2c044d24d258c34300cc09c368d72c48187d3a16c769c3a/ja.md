```
get_header(con::SeisCon, name::String)
```

`con`内のすべての`BlockScan`からメタデータの要約`name`を取得します。列1にはブロック内の`name`の最小値が含まれ、列2にはブロック内の`name`の最大値が含まれます。Src/Recスケーリングは適用されません。

ソース座標ペアを配列として取得するには、`get_sources`を参照してください。

# 例

trace = get_header(s, "TraceNumber") ```
