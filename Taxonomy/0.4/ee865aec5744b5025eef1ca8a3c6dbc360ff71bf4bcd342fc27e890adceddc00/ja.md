```
get(db::Taxonomy.DB, taxid::Int, default)
```

指定された taxid に対して保存されている `Taxon` オブジェクトを返すか、taxid に対するマッピングが存在しない場合は指定されたデフォルト値を返します。
