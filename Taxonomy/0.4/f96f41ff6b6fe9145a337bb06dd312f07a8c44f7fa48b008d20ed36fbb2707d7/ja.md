```
get(db::Taxonomy.DB, idx::Union{Int,Symbol}, default)
```

指定された taxid またはランク (すなわち :phylum) に対して保存されている Taxon オブジェクトを返します。taxid に対するマッピングが存在しない場合は、指定されたデフォルト値を返します。
