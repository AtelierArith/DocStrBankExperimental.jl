```
formatted_response(model::String, prompt::String; params::Dict{String,Any}=Dict{String,Any}())
```

チャットの完了を作成し、フォーマットされた応答を返します。

引数:     model (String): 完了に使用するモデルの名前。     prompt (String): 完了に使用するプロンプト。     params (Dict{String,Any}, オプション): APIに渡す追加のパラメータ。デフォルトはDict{String,Any}()。

返り値:     String: APIからのフォーマットされた応答。
