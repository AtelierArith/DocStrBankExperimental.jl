```
Taxon(taxid::Int, db::Taxonomy.DB)
Taxon(taxid::Int)
```

`taxid`から`Taxon`を構築します。`db`を省略すると、通常は最後に作成されたデータベースである`current_db()`が自動的に呼び出されます。
