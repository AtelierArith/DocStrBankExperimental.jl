```
occurrence_request(sp::Species; kw...)
occurrence_request(; kw...)
```

発生ダウンロードをリクエストし、後でダウンロードURLを提供するトークンを返します。準備ができたら`occurrence_download(token)`を呼び出すことができます。それまでは404エラーが表示されます。

# 例

ここでは、一般的なミナミコウモリ、*Acridotheres tristis*のすべての発生をダウンロードするリクエストを行います。

```
julia> sp = species_match("Acridotheres tristis");

julia> occurrence_count(sp)
1936341
julia> token = occurrence_request(sp, username="my_gbif_username")
```

これにより、パスワードの入力が求められ、エラーが発生するか、後で`occurrence_download`で使用するための`token`の値が返されます。

トークンを保存するのを忘れ、セッションがまだ開いている場合は、`occurrence_download()`を使用して最新のリクエストをダウンロードできます。

# キーワード

  * `username`: gbif.orgアカウントの文字列ユーザー名
  * `password`: gbif.orgアカウントの文字列パスワード。このキーワードが使用されていない場合、REPLでパスワードが入力されます。
  * `type`: `:and`または`:or`クエリから選択します。

許可されているクエリキーワードは次のとおりです: `(:datasetKey, :year, :month, :decimalLatitude, :decimalLongitude, :elevation, :depth, :institutionCode, :collectionCode, :catalogNumber, :scientificName, :occurrenceID, :establishmentMeans, :degreeOfEstablishment, :pathway, :eventDate, :modified, :lastInterpreted, :basisOfRecord, :countryCode, :continent, :publishingCountry, :recordedBy, :identifiedBy, :recordNumber, :typeStatus, :hasCoordinate, :hasGeospatialIssues, :mediaType, :issue, :kingdomKey, :phylumKey, :classKey, :orderKey, :familyKey, :genusKey, :subgenusKey, :speciesKey, :acceptedTaxonKey, :taxonomicStatus, :repatriated, :organismID, :locality, :coordinateUncertaintyInMeters, :stateProvince, :waterBody, :level0Gid, :level1Gid, :level2Gid, :level3Gid, :protocol, :license, :publishingOrgKey, :hostingOrganizationKey, :crawlId, :installationKey, :networkKey, :eventID, :parentEventID, :samplingProtocol, :projectId, :programmeAcronym, :verbatimScientificName, :taxonID, :sampleSizeUnit, :sampleSizeValue, :organismQuantity, :organismQuantityType, :relativeOrganismQuantity, :collectionKey, :institutionKey, :recordedByID, :identifiedByID, :occurrenceStatus, :lifeStage, :isInCluster, :dwcaExtension, :iucnRedListCategory, :datasetID, :datasetName, :otherCatalogNumbers, :preparations)`

# 修飾子

パラメータ値は、ペアを使用して一致の種類を変更できます: `elevation = :lessThan => 100`、またはjuliaのFix2演算子を使用して`elevation = >(100)`のようにします。

| ペアキー                 |  Fix2 | 説明                              |
|:-------------------- | -----:|:------------------------------- |
| :equals              | ==(x) | 等価比較                            |
| :lessThan            |  <(x) | より小さい                           |
| :lessThanOrEquals    | <=(x) | より小さいか等しい                       |
| :greaterThan         | =>(x) | より大きい                           |
| :greaterThanOrEquals | >=(x) | より大きいか等しい                       |
| :in                  | in(x) | 比較する複数の値を指定                     |
| :not                 | !=(x) | 論理的否定                           |
| :and                 |  &(x) | 論理AND（論理積）                      |
| :or                  |       | (x)                             |
| :like                |       | パターンを検索、?は1文字に一致し、*は0文字以上に一致します |

# 値の代わりに渡すには:

|:isNull    | 空の値を持つ    | |:isNotNull | 空でない値を持つ |
