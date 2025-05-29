```
unfold(vf::VectorFold; from=1, to=folds(vf))
```

`vf`の展開されたバージョンを構築します（`pattern(vf)`と同じ型で）。`vf`にイテレータを使用することでメモリ割り当てを回避できますが、`unfold`の場合はそうではありません。
