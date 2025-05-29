```
files_download(auth::Authorization,
               path::String
              )::Tuple{FileMetadata, Vector{UInt8}}
```

ファイル `path` をダウンロードします。メタデータとコンテンツの両方を返します。
