```
MachOLoadDylibCmd
```

このMach-Oファイルが正しくリンクされるために読み込む必要があるdylibに関する情報を提供するロードコマンドです。このロードコマンドのAPIは以下のようになります。

### 作成:

  * MachOLoadCmd()

### アクセサ:

  * dylib_name()
  * dylib_timestamp()
  * dylib_version()
  * dylib_compatibility()
