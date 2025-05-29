```
ogr2ogr(indata, options=String[]; dest="/vsimem/tmp", kwargs...)
```

### パラメータ

  * `indata` ソースデータセット。
  * `options` オプションのリスト（ファイル名やオープンオプションを含む可能性があります）。受け入れられるオプションはgdalwarpユーティリティのものです。
  * `kw` はGMT領域（-R）、プロジェクション（-J）、インクリメント（-I）および `save=fname` オプションを含む可能性のあるkwargsです。

### 戻り値

GMTデータセット、またはGDALデータセット（またはファイルがディスクに書き込まれた場合は何も返しません）。
