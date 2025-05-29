```
function import_project_info(; format=nothing, data, url=get_url(), token=get_token(),)
```

REDCapプロジェクトの基本属性をインポートします

# 名前付き引数

  * `url`: (デフォルトでは`ENV["REDCAP_API_URL"]`から読み取ります)
  * `token`: REDCapプロジェクトおよびユーザー名に特有のAPIトークン (デフォルトでは`ENV["REDCAP_API_TOKEN"]`から読み取ります)
  * `data`: 文字列、ファイル名、またはNamedTupleやDictなどのデータ型である可能性があります。利用可能な属性はproject*title、project*language、purpose、purpose*other、project*notes、custom*record*label、secondary*unique*field、is*longitudinal、surveys*enabled、scheduling*enabled、record*autonumbering*enabled、randomization*enabled、project*irb*number、project*grant*number、project*pi*firstname、project*pi*lastname、display*today*now*button、iand bypass*branching*erase*field_promptです。
  * `format`: `data`入力パラメータのフォーマット: `:csv`、`:json`、または`:xml`（デフォルト）。`data`が文字列またはファイル名の場合、この値は正しいフォーマットを示す必要があります。`data`がNamedTuple、Dict、または類似の型の場合、この値は内部でデータを渡すために使用されるフォーマットを決定します。
