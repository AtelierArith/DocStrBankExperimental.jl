```
files_upload(auth::Authorization,
             path::String,
             content::Vector{UInt8}
            )::FileMetadata
```

バイト配列 `content` をファイル `path` にアップロードし、そのメタデータを返します。この関数は小さなファイル（< 150 MByte）のみで使用するべきであり、アップロードするファイルが少ない場合に限ります。他の `files_upload` 関数は、大きなファイルや多数のファイルをアップロードする場合により効率的です。
