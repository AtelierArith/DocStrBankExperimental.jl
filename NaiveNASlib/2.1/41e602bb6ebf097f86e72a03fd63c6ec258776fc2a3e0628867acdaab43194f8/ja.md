```
remove_edge!(from::AbstractVertex, to::AbstractVertex; [nr], [strategy])
```

`from` から `to` へのエッジを削除します。

`from` から `to` へのエッジが複数ある場合、`nr` を使用してどのエッジを削除するかを区別できます。

サイズは指定された `strategy` に基づいて調整されます。
