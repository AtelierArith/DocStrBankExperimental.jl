```
function export_project_XML(; url=get_url(), token=get_token(), returnFormat=nothing, returnMetadataOnly=nothing, records=nothing, fields=nothing, events=nothing, exportSurveyFields=nothing, exportDataAccessGroups=nothing, filterLogic=nothing, exportFiles=nothing,)
```

REDCapプロジェクト全体をXMLプロジェクトファイルとしてエクスポートします。これは新しいプロジェクトを作成するために使用できます。

# 名前付き引数

  * `url`: (デフォルトで`ENV["REDCAP_API_URL"]`から読み取る)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで`ENV["REDCAP_API_TOKEN"]`から読み取る)
  * `returnFormat`: 希望する出力形式: `:csv`、`:json`、または`:xml` (デフォルト)
  * `records`: 出力をこれらのレコード名に制限することができます (スカラーまたはベクトル)
  * `fields`: 出力をこれらのフィールド名に制限することができます (スカラーまたはベクトル)
  * `events`: 出力をこれらのユニークなイベント名に制限することができます (スカラーまたはベクトル)
  * `returnMetadataOnly`: データなしでメタデータのみを返すことができます (デフォルトはfalse)
  * `exportSurveyFields`: アンケート識別子およびタイムスタンプフィールドをエクスポートすることができます (デフォルトはfalse)
  * `exportDataAccessGroups`: `redcap_data_access_group`フィールドをエクスポートすることができます (デフォルトはfalse)
  * `exportFiles`: ファイルアップロードおよび署名フィールドの内容を含めることができます (デフォルトはfalse)
  * `filterLogic`: レコードをフィルタリングするためのロジック文字列
