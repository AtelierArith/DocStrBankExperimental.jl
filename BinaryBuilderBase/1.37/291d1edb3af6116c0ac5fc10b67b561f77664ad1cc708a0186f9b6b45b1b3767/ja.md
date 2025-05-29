```
ArchiveSource(url::String, hash::String; unpack_target::String = "")
```

インターネットから `url` からダウンロードされるサポートされているアーカイブ形式のリモートアーカイブ（例：TARまたはZIPボール）を指定します。 `hash` はファイルの64文字のSHA256チェックサムです。

ビルダー環境では、アーカイブは自動的に `${WORKSPACE}/srcdir` に展開されるか、提供された場合はオプションのキーワード `unpack_target` が指すサブディレクトリに展開されます。
