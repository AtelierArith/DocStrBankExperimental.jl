```
D = maregrams(list=false, code="", name="", days::Real=2, starttime::String="", printurl=false)::GMTdataset
D = maregrams(lon::Real, lat::Real; days=2, starttime::String="")::GMTdataset
```

http://www.ioc-sealevelmonitoring.org からmaregramsデータをダウンロードします。

デフォルトでは、過去2日間のデータをダウンロードしますが、長さと期間は入力オプションによって設定可能です。この関数を使用するには、ステーションコードまたは名前を知っている必要があるため、座標を使用して最寄りのステーションを見つける可能性も提供しています。ステーションのデータの位置と名前が記載されたファイルは `TESTSDIR/assets/maregs_online.csv` に保存されており、`d = GMT.read_maregrams()` を使用してアクセスでき、その内容は `d` 辞書に返されます。すべてのステーションサイトが常に稼働しているわけではないため、一部のステーションからデータをリクエストする際にエラーが発生することは、残念ながらそれほど珍しくありません。

私たちの参照ステーションデータは少し古く（更新が必要）、http://www.ioc-sealevelmonitoring.org サイトにリストされているより多くのステーションをオンラインで見つけることができます。ユーザーが知らないステーションコードを提供した場合でも、それが有効なものであれば、そのステーションのデータを返します。例: `D = maregrams(code="tdoj")`

### 引数

  * `lon, lat`: （第二の形式）その点に最も近いステーションを見つけるために使用される点の座標。これは、`code` または `name` を使用する代わりにステーションを選択するための代替方法です。

### キーワード引数

  * `list`: `true` に等しい場合、すべての利用可能なステーションとそのコードおよび座標のリストを含むGMTdatasetを返します。文字列の場合、その文字列を含むすべてのエントリを検索します。*例:* `list=Canada` はカナダのすべてのステーションを返します。
  * `code`: ステーションコード（`list` の出力を参照）
  * `name`: `code` の代わりにステーション名を指定します（`list` の出力を参照）
  * `days`: ダウンロードする日数。小数点数にすることができます。
  * `starttime`: ISO8601形式の開始時間（*例* `"2019-01-01T00:00:00"`、または単に日付 `"2019-01-01"`）。
  * `printurl`: `true` の場合、ステーションのURLを印刷します。ステーションとそのデータに関する詳細情報を取得するのに便利です。

### 戻り値

  * `D`: maregramsデータを含むGMTdataset。

### 例

2025年2月1日から始まる4日間の時系列を、コード "lgos"（ポルトガルのラゴス）のステーションについて取得します。

```julia
D = maregrams(code="lgos", days=4, starttime="2025-02-01")
viz(D, title="Tide Gauge at Lagos (Portugal)")
```
