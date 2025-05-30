```
create_completion(model::String, prompt::String; params::Dict{String,Any}=Dict{String,Any}())
```

チャット補完を作成します。

引数:     model (String): 補完に使用するモデルの名前。     prompt (String): 補完に使用するプロンプト。     params (Dict{String,Any}, オプション): APIに渡す追加のパラメータ。デフォルトはDict{String,Any}()。

戻り値:     Any: APIからの応答。
