```
create_edge!(from::AbstractVertex, to::AbstractVertex; [pos], [strategy])
```

`from` から `to` へのエッジを [`inputs(to)`](@ref) のインデックス `pos` に作成します。

サイズは指定された `strategy` に基づいて調整されます。
