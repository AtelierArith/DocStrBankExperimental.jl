```
VizierCatalog(id, [cols=All()]; [unitful=false])
```

[VizieR](https://vizier.u-strasbg.fr/) データベースからのカタログで、`id`（例: `"J/ApJS/260/4/table2"`）によって識別されます。

主な機能:

  * 生ファイルとしてダウンロード: `download(::VizierCatalog)`
  * Julia テーブル（`StructArray`）として取得: `table(::VizierCatalog)`
  * [CDS X-Match サービス](https://cdsxmatch.u-strasbg.fr/xmatch)を使用したクロスマッチ: `FlexiJoins` インターフェース、`innerjoin((; ::VizierCatalog, tbl), by_distance(identity, ..., separation, <=(...)))`

引数はカタログへのアクセスや処理を制御します:

  * `cols=All()`: 選択した列のみを取得
  * `unitful=false`: 単位を持つ列を `Unitful.jl` 値に解析するかどうか
  * `table_format="votable"`: ダウンロードするテーブルの形式で、生ファイルのダウンロードのみサポートされています
