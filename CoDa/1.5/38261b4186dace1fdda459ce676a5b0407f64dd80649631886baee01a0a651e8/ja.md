```
compose(table, colnames; keepcols=true, as=:coda)
```

`table`の列`colnames`を合成の一部に変換し、結果を[`CoDaArray`](@ref)に保存します。`keepcols`が`true`に設定されている場合、結果を新しいテーブルの列として保存し、他のすべての列を保持します。
