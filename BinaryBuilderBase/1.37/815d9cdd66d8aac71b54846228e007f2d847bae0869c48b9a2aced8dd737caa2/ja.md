```
download_source(source::AbstractSource; verbose::Bool = false)
```

指定された `source` をダウンロードします。すべてのダウンロードは、BinaryBuilder の `downloads` ストレージディレクトリ内にキャッシュされます。
