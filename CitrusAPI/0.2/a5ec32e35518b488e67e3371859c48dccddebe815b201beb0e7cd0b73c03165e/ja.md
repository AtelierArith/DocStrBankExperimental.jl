```
list_surveys(client; username=nothing)
list_surveys(client, sink; username=nothing)
```

LimeSurveyインスタンスのすべての調査をリストします。オプションの引数`username`を設定すると、特定のユーザーに属するすべての調査をリストできます。

`sink`を指定して、応答を別のデータ構造に解析します。

参照: [https://api.limesurvey.org/classes/remotecontrol*handle.html#method*list_surveys](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_list_surveys)

# 例

```julia-repl
julia> # Limesurveyクライアントcに接続
julia> list_surveys(c)

julia> using DataFrames
julia> list_surveys(c, DataFrame)
```
