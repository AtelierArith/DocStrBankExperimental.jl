```
name2taxids(name::AbstractString, db::Taxonomy.DB)
name2taxids(name::AbstractString)
```

`name`からその`taxid`の`Vector`を返します。`name`は科学名と正確に一致する必要があります。複数のヒットが見つかった場合は、複数要素の`Vector`を返します。見つからなかった場合は、1要素または0要素の`Vector`を返します。`db`を省略すると、自動的に`current_db()`が呼び出され、通常は最後に作成されたデータベースになります。
