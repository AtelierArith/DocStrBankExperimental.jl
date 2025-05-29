```
files_upload(auth::Authorization,
             upload_spec_channel::Union{AbstractChannel{UploadSpec},
                                        AbstractVector{UploadSpec}}
            )::Vector{FileMetadata}
```

複数のファイルを同時に効率的にアップロードします。アップロード仕様チャネルは、アップロードされるファイルを説明するために使用されます。このチャネルは、すべてのアップロード仕様を渡した後に閉じる必要があります。戻り値は、アップロードされたファイルのすべてのメタデータのベクターです。

この関数は、多くのファイルがアップロードされる場合に効率的です。
