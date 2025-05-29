```
google_download(url::AbstractString, location::Union{AbstractString,AbstractCmd,IO})
```

GoogleのURL `url` からデータを `location` にダウンロードし、`location` を返します。

`location` は `Downloads.download` が受け入れる任意の型であることができます - つまり、ファイルパス、コマンド、またはIOバッファです。
