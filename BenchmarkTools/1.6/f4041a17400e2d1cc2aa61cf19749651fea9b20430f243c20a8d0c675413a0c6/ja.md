```
clear_empty!(group::BenchmarkGroup)
```

`group`から空のサブグループを再帰的に削除します。

これは、`g=BenchmarkGroup(); g[1]`のように誤ったフィールドにアクセスした後に`BenchmarkGroup`を剪定するために使用しますが、`g[1]`に何も保存しないため、空のサブグループ`g[1]`が作成されます。
