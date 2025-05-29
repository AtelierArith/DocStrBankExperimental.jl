```
isempty(group::BenchmarkGroup)
```

`group`が空であれば`true`を返します。これは最初に`group`に対して`clear_empty!`を実行し、空のサブグループを再帰的に削除します。
