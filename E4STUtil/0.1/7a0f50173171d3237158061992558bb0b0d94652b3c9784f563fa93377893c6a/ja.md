```
save_metadata(file::String, description::String) -> metadata
```

`file`のメタデータを`joinpath(dirname(file), "metadata.yml")`に保存し、必要に応じて作成します。
