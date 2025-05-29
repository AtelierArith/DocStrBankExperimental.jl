```
function import_users(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, data,)
```

REDCapプロジェクトにユーザーとユーープリビレッジをインポートします

# 名前付き引数

  * `url`: (デフォルトで `ENV["REDCAP_API_URL"]` から読み取ります)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトで `ENV["REDCAP_API_TOKEN"]` から読み取ります)
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります。利用可能な属性は、username、expiration、data*access*group、design、alerts、user*rights、data*access*groups、data*export、reports、stats*and*charts、manage*survey*participants、calendar、data*import*tool、data*comparison*tool、logging、email*logging、file*repository、data*quality*create、data*quality*execute、api*export、api*import、api*modules、mobile*app、mobile*app*download*data、record*create、record*rename、record*delete、lock*records*customization、lock*records、lock*records*all*forms、forms、およびforms_exportです。
  * `format`: `data`入力パラメータのフォーマット: `:csv`、`:json`、または`:xml` (デフォルト)。`data`が文字列またはファイル名の場合、この値は正しいフォーマットを示す必要があります。`data`がNamedTuple、Dict、または類似の型の場合、この値はデータを内部的に渡すために使用されるフォーマットを決定します。
  * `returnFormat`: 希望する出力フォーマット: `:csv`、`:json`、または`:xml` (デフォルト)
