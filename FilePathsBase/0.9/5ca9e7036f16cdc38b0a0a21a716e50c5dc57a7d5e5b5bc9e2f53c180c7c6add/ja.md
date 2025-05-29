```
download(url::Union{AbstractString, AbstractPath}, localfile::AbstractPath)
```

リモート `url` からファイルをダウンロードし、`localfile` パスに保存します。

注意: `localfile` ディレクトリにダウンロードしないことは、基本的な Julia の動作と一致します。 https://github.com/rofinn/FilePathsBase.jl/issues/48
