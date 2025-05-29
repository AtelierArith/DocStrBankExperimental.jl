```
read_template(data_path::String)
```

指定された `data_path` の JSON ファイルからプロンプトテンプレートを読み込みます。この関数は JSON データを解析し、メタデータ、システム、およびユーザーメッセージを含む `PromptTemplate` オブジェクトを構築します。TODO: 解析する前に、スキーマに対して JSON データを検証して、有効であることを確認します。

# 引数

  * `data_path::String`: プロンプトテンプレートを含む JSON ファイルへのパス。

# 戻り値

  * `PromptTemplate`: メタデータ、システム、およびユーザーメッセージをカプセル化した `PromptTemplate` 構造体。

# 発生する例外

  * `ErrorException`: テンプレートが仕様フォーマットに一致しない場合。
