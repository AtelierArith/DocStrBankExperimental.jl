```
download(rfs::RemoteFileSet;
    quiet::Bool=false, verbose::Bool=false, force::Bool=false)
```

`rfs`に含まれるすべてのファイルをダウンロードします。

  * `quiet`: メッセージを表示しない。
  * `verbose`: すべてのメッセージを表示する。
  * `force`: ダウンロードを強制し、既存のファイルを上書きする。
  * `force_update`: 既存のファイルが等しい場合でも上書きする。
