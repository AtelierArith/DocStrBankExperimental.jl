```
write_nexus(fname::String,tree::FelNode)
```

木をnexusファイルとして書き込みます。これは、例えばFigTreeで開くのに適しています。`node_data`辞書内のデータは注釈に変換されます。単純な`node_data`形式とタイプのみでテストされています。
