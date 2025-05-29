```
occurrence_search(species::Species; kw...)
occurrence_search([q]; kw...)
occurrence_search(q, returntype; limit...)
```

発生を検索し、`Table{Occurrence}` テーブルを返します。

# 例

ここでは `species_match` を使用して種を見つけ、その後 `occurrence_search` で全ての発生を取得します。

```julia
julia> 
using GBIF2

julia> 
sp = species_match("Falco punctatus");

julia> 
ocs = occurrence_search(sp; continent=:AFRICA, limit=1000)
[ Info: 522 occurrences found, limit was 1000
522-element GBIF2.Table{GBIF2.Occurrence, Vector{JSON3.Object}}
┌──────────────────┬─────────────────┬────────┬────────┬────────┬────────────
│ decimalLongitude │ decimalLatitude │   year │  month │    day │  kingdom  ⋯
│         Float64? │        Float64? │ Int64? │ Int64? │ Int64? │  String?  ⋯
├──────────────────┼─────────────────┼────────┼────────┼────────┼────────────
│          missing │         missing │   2012 │      8 │     18 │ Animalia  ⋯
│          missing │         missing │   2010 │      1 │     29 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     10 │     26 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      4 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      4 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│        ⋮         │        ⋮        │   ⋮    │   ⋮    │   ⋮    │    ⋮      ⋱
└──────────────────┴─────────────────┴────────┴────────┴────────┴────────────
                                              78 columns and 507 rows omitted
```

# 引数

  * `q`: 検索クエリ。
  * `species`: 最初の値が種である場合、検索キーワードがそこから取得されます。
  * `returntype`: `Symbol` から返す型を変更します：

      * `:catalogNumber`: 一致するカタログ番号を返す検索。テーブルは関連性に基づいて順序付けられます。
      * `:collectionCode`: 一致するコレクションコードを返す検索。テーブルは関連性に基づいて順序付けられます。
      * `:occurrenceId`: 一致する発生識別子を返す検索。テーブルは関連性に基づいて順序付けられます。
      * `:recordedBy`: 一致する収集者名を返す検索。テーブルは関連性に基づいて順序付けられます。
      * `:recordNumber`: 一致する記録番号を返す検索。テーブルは関連性に基づいて順序付けられます。
      * `:institutionCode`: 一致する機関コードを返す検索。テーブルは関連性に基づいて順序付けられます。

# キーワード

パラメータは [GBIF api](https://www.gbif.org/developer/species) とまったく同じように使用します。

キーワードの列挙値は `[GBIF2.enum](@ref)` 関数で見つけることができます。

GBIFの範囲クエリは、値を `Tuple` に入れることで機能します。例： `elevation=(10, 100)`。

  * `basisOfRecord`: 記録の基礎、私たちの BasisOfRecord 列挙型で定義されています。
  * `catalogNumber`: ソースによって物理コレクションまたはデジタルデータセット内に割り当てられた任意の形式の識別子で、ユニークではない可能性がありますが、機関およびコレクションコードと組み合わせることでかなりユニークであるべきです。
  * `classKey`: クラス分類キー。
  * `collectionCode`: ソースによって機関の文脈内で物理コレクションまたはデジタルデータセットを一意に識別するために割り当てられた任意の形式の識別子。
  * `continent`: 私たちの Continent 列挙型で定義された大陸。
  * `coordinateUncertaintyInMeters`: 与えられた decimalLatitude と decimalLongitude からの水平距離（メートル単位）で、位置全体を含む最小の円を記述します。範囲クエリをサポートします。
  * `country`: 発生が記録された国の2文字の国コード（ISO-3166-1に準拠）。
  * `crawlId`: この記録を収集したクローラーの試行。
  * `datasetId`: データセットのID。
  * `datasetKey`: 発生データセットキー（UUID）。
  * `datasetName`: データセットの名前。
  * `decimalLatitude`: WGS 84に基づく-90から90の間の小数での緯度。範囲クエリをサポートします。
  * `decimalLongitude`: WGS 84に基づく-180から180の間の小数での経度。範囲クエリをサポートします。
  * `depth`: 高度に対するメートル単位の深さ。例えば、与えられた高度の湖面から10メートル下。範囲クエリをサポートします。
  * `elevation`: 海面上のメートル単位の標高（高度）。範囲クエリをサポートします。
  * `establishmentMeans`: EstablishmentMeans、私たちの EstablishmentMeans 列挙型で定義されています。
  * `eventDate`: ISO 8601形式の発生日：`yyyy`、`yyyy-MM`、`yyyy-MM-dd`、または `MM-dd`。範囲クエリをサポートします。
  * `eventId`: サンプリングイベントに関連する情報の識別子。
  * `facet`: フィールドの最も頻繁な値を取得するために使用されるファセット名。ファセットは、eventDate、geometry、lastInterpreted、locality、organismId、stateProvince、waterBodyを除くすべてのパラメータで許可されます。このパラメータは、複数のファセットを要求するために繰り返すことができます。例：/occurrence/search?facet=datasetKey&facet=basisOfRecord&limit=0
  * `facetMincount`: ファセットパラメータと組み合わせて使用されます。facetMincountNを設定して、カウントがN未満のファセットを除外します。例：/search?facet=type&limit=0&facetMincount=10000は、'OCCURRENCE'というタイプ値のみを表示します。なぜなら、'CHECKLIST'と'METADATA'は10000未満のカウントを持っているからです。
  * `facetMultiselect`: ファセットパラメータと組み合わせて使用されます。facetMultiselect=trueを設定すると、現在フィルタリングされていない値のカウントも返されます。例：/search?facet=type&limit=0&type=CHECKLIST&facetMultiselect=trueは、type=CHECKLISTでフィルタリングされているにもかかわらず、'OCCURRENCE'と'METADATA'のタイプ値を表示します。
  * `facetOffset`:
  * `facetLimit`: ファセットパラメータは、facetOffsetおよびfacetLimitを使用してページングリクエストを許可します。例：/occurrence/search?facet=datasetKey&datasetKey.facetLimit=5&datasetKey.facetOffset=10&limit=0
  * `familyKey`: 科分類キー。
  * `format`: エクスポート形式、TSV（デフォルト）およびCSVを受け入れます。
  * `fromDate`: 日付範囲の開始部分日付、`yyyy-MM`形式を受け入れます。例：`2015-11`
  * `gadmGid`: 任意のレベルのGADM地理識別子。例：AGO、AGO.1*1、AGO.1.1*1またはAGO.1.1.1_1
  * `gadmLevel`: GADM地域レベル、有効な値は0から3まで。
  * `gadmLevel0Gid`: ゼロレベルのGADM地理識別子。例：AGO
  * `gadmLevel1Gid`: 第一レベルのGADM地理識別子。例：AGO.1_1
  * `gadmLevel2Gid`: 第二レベルのGADM地理識別子。例：AFG.1.1_1
  * `gadmLevel3Gid`: 第三レベルのGADM地理識別子。例：AFG.1.1.1_1
  * `genusKey`: 属分類キー。
  * `geoDistance`: 指定された距離内の座標値を持つ発生記録と一致するようにフィルタリングします。単位をサポートします：in（インチ）、yd（ヤード）、ft（フィート）、km（キロメートル）、mmi（海里）、mm（ミリメートル）、cm（センチメートル）、mi（マイル）、m（メートル）。例：/occurrence/search?geoDistance=90,100,5km
  * `geometry`: Well Known Text（WKT）形式で記述されたポリゴン内の発生を検索します。POINT、LINESTRING、LINEARRING、POLYGONおよびMULTIPOLYGONのみが受け入れられるWKTタイプです。例えば、POLYGON ((30.1 10.1, 40 40, 20 40, 10 20, 30.1 10.1))として書かれた形状は、そのままクエリされます。すなわち、/occurrence/search?geometry=POLYGON((30.1 10.1, 40 40, 20 40, 10 20, 30.1 10.1))。ポリゴンは反時計回りの点の順序を持たなければならず、そうでない場合は予測不可能な結果をもたらします。（時計回りのポリゴンは反対の領域を表します：地球の表面に「穴」がある。こうしたクエリはサポートされていません。）
  * `hasCoordinate`: 緯度と経度の両方に値を含む発生記録に検索を制限します（すなわち、`hasCoordinate=true`は座標値を持つ発生記録に制限し、`hasCoordinate=false`は座標値を持たない発生記録に制限します）。
  * `hasGeospatialIssue`: 空間的な問題を含む/除外する発生記録（私たちの記録解釈で決定された）を含めます。すなわち、hasGeospatialIssue=trueは空間的な問題を持つ記録のみを返し、hasGeospatialIssue=falseは空間的な問題を持たない記録のみを含めます。このパラメータがない場合は、空間的な問題の有無にかかわらず任意の記録が返されます。
  * `hl`: フルテキスト検索フィールドでクエリに一致する用語を強調表示するには、hl=trueを設定します。強調表示は、クラス 'gbifH1' の強調タグになります。例：/search?q=plant&hl=true。フルテキスト検索フィールドには、タイトル、キーワード、国、出版国、出版組織のタイトル、ホスティング組織のタイトル、および説明が含まれます。メタデータ文書からの情報を含む追加のフルテキストフィールドが検索されますが、このフィールドのテキストは応答に返されません。
  * `identifiedBy`: 発生の分類学的同定を提供した人物。
  * `identifiedByID`: 発生の分類学的同定を提供した人物の識別子（例：ORCID）。
  * `institutionCode`: 記録が属する機関を識別するためにソースによって割り当てられた任意の形式の識別子。ユニークであることは保証されていません。
  * `issue`: 私たちの OccurrenceIssue 列挙型で定義された特定の解釈の問題。
  * `kingdomKey`: 王国分類キー。
  * `lastInterpreted`: この記録がGBIFで最後に変更された日付、ISO 8601形式：`yyyy`、`yyyy-MM`、`yyyy-MM-dd`、または `MM-dd`。範囲クエリをサポートします。これは、GBIFで最後に変更された日付であり、必ずしも発行者によって最初/最後に変更された日付ではありません。データは、分類学的バックボーン、地理データソース、または解釈プロセスを変更すると再解釈されます。
  * `license`: データセットまたは記録に適用されるライセンスの種類。
  * `limit`: 返す結果の最大数。この値は300を超えることはできず、それ以上の値は300に設定されます。
  * `locality`: 場所の具体的な説明。
  * `mediaType`: 発生に関連付けられたマルチメディアの種類、私たちの MediaType 列挙型で定義されています。
  * `modified`: 出版者によるリソースが変更された最も最近の日付時刻。
  * `month`: 年の月、1月は1から始まります。範囲クエリをサポートします。
  * `networkKey`: 発生が属するGBIFネットワーク。
  * `occurrenceId`: 出版者によって提供された発生記録の単一のグローバルにユニークな識別子。
  * `occurrenceStatus`: 'ABSENT'または'PRESENT'のいずれか；発生の存在または不在。
  * `offset`: 結果を開始するオフセット。
  * `orderKey`: 順序分類キー。
  * `organismId`: 生物インスタンスの識別子（特定の生物のデジタル記録とは異なる）。グローバルにユニークな識別子またはデータセット特有の識別子である可能性があります。
  * `organismQuantity`: 生物の数量の数値または列挙値。
  * `organismQuantityType`: 生物の数量に使用される定量化システムのタイプ。
  * `otherCatalogNumbers`: 前のまたは代替の完全に修飾されたカタログ番号。
  * `phylumKey`: 門分類キー。
  * `preparations`: 標本の準備または保存方法。
  * `programme`: 特定の資金源に関連付けられた活動のグループ、例えばGBIF BIDプログラム。
  * `projectId`: プロジェクトの識別子、通常は資金提供プログラムによって割り当てられます。
  * `protocol`: 発生記録を提供するために使用されるプロトコルまたはメカニズム。
  * `publishingCountry`: 所有組織の国の2文字の国コード（ISO-3166-1に準拠）。
  * `publishingOrg`: 出版組織キー（UUID）。
  * `publishingOrgKey`: 出版組織キー（UUID）。
  * `q`: 簡単な検索パラメータ。このパラメータの値は、単語またはフレーズのいずれかです。
  * `recordedBy`: 発生を記録した人物。
  * `recordedByID`: 発生を記録した人物の識別子（例：ORCID）。
  * `recordNumber`: 現場で記録された時に記録に与えられた識別子。
  * `relativeOrganismQuantity`: 生物の数量の相対的な測定（すなわち、絶対単位なし）。
  * `repatriated`: 発行国が記録が記録された国と異なる記録を検索します。
  * `sampleSizeUnit`: サンプリングイベントにおけるサンプルのサイズ（時間の長さ、長さ、面積、または体積）の測定単位。
  * `sampleSizeValue`: サンプリングイベントにおけるサンプルのサイズ（時間の長さ、長さ、面積、または体積）の測定値。
  * `samplingProtocol`: サンプリングイベント中に使用された方法またはプロトコルの名前、参照、または説明。
  * `scientificName`: GBIFバックボーンからの科学名。すべての含まれるおよび同義の分類群が検索に含まれます。内部的には、最初に種マッチサービスに呼び出してtaxonKeyを取得します。ユニークな科学名のみが結果を返し、同名異義語（多くの単名）は何も返しません！代わりにtaxonKeyパラメータを使用し、種マッチサービスを直接使用することを検討してください。
  * `speciesKey`: 種分類キー。
  * `stateProvince`: 場所が発生する国よりも小さい次の行政区域の名前（州、県、カントン、部門、地域など）。
  * `subgenusKey`: 亜属分類キー。
  * `taxonKey`: GBIFバックボーンからの分類群キー。すべての含まれるおよび同義の分類群が検索に含まれます。したがって、taxonKey=212での鳥類の検索（すなわち、`coordinate_search(; taxonKey=212)`）は、どの種であってもすべての鳥に一致します。
  * `toDate`: 日付範囲の終了部分日付、`yyyy-MM`形式を受け入れます。例：`2019-12`
  * `typeStatus`: 主題に適用される命名上のタイプ（タイプステータス、典型的な科学名、出版）。
  * `userCountry`: リクエストを行ったユーザーの国。
  * `verbatimScientificName`: データ発行者によってGBIFに提供された科学名、解釈および処理の前。
  * `verbatimTaxonId`: データ発行者によってGBIFに提供された分類群識別子。
  * `waterBody`: 場所が発生する水域の名前。
  * `year`: 4桁の年。`98`の年はAD 98として解釈されます。範囲クエリをサポートします。

```
