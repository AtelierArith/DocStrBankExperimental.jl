```
format_template(template::PromptTemplate; kwargs...)::Prompt
```

`PromptTemplate`をフォーマットし、システムおよびユーザーメッセージ内のすべての変数をユーザーが提供した値で置き換えます。

# 引数

  * `template::PromptTemplate`: メタデータ、システム、およびユーザーメッセージを含むプロンプトテンプレート。
  * `kwargs...`: キーが変数名で、値が対応する置き換えである可変数のキーワード引数。

# 戻り値

  * `Prompt`: 置き換えられた値を含むシステムおよびユーザーメッセージを持つ`Prompt`構造体。

# 発生する例外

  * `ErrorException`: システムまたはユーザーテンプレートで指定された変数が`kwargs`に存在しない場合。
  * `Warning`: テンプレートで使用されていない余分な`kwargs`がある場合。
