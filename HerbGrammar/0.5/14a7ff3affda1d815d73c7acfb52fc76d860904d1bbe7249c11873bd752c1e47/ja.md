```
remove_rule!(g::AbstractGrammar, idx::Int)
```

`idx`に対応するルールを文法から削除します。インデックスのシフトを避けるために、ルールは`nothing`で置き換えられ、他のすべてのデータ構造がそれに応じて更新されます。
