```
listartifacts(instance::MLFlow, run_id::String; path::String="", page_token::String="")
listartifacts(instance::MLFlow, run::Run; path::String="", page_token::String="")
```

[`Run`](@ref) のアーティファクトをリストします。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run_id`: アーティファクトをリストする [`Run`](@ref) の ID。
  * `path`: このパスに一致するアーティファクトをフィルタリングします（ルートアーティファクトディレクトリからの相対パス）。
  * `page_token`: 取得するアーティファクト結果のページを示すトークン。

# 戻り値

  * [`Run`](@ref) のルートアーティファクトディレクトリ。
  * アーティファクトのファイル位置とメタデータのリスト。
  * 次のページのアーティファクト結果を取得するために使用できるトークン。
