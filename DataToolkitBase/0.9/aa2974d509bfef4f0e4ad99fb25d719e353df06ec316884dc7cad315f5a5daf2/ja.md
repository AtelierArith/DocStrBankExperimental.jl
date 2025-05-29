```
save(writer::Datasaveer{driver}, destination::Any, information::Any)
```

特定の `writer` を使用して、`information` を `destination` に保存します。

これは全体のデータフローのこのコンポーネントを満たします：

```
Data          Information
  ▲               ╷
  ╰────writer─────╯
```
