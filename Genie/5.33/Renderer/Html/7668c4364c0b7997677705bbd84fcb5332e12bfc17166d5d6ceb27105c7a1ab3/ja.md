```
html(data::String; context::Module = @__MODULE__, status::Int = 200, headers::HTTPHeaders = HTTPHeaders(), layout::Union{String,Nothing} = nothing, vars...) :: HTTP.Response
```

`data`入力をHTMLとして解析し、HTML HTTPレスポンスを返します。

# 引数

  * `data::String`: レンダリングされるHTML文字列
  * `context::Module`: 変数が評価されるモジュール（varsのスコープを提供するため）。通常はコントローラー。
  * `status::Int`: レスポンスのステータスコード
  * `headers::HTTPHeaders`: HTTPレスポンスヘッダー
  * `layout::Union{String,Nothing}`: `data`をレンダリングするためのレイアウトファイル

# 例

```jldoctest
julia> html("<h1>Welcome $(vars(:name))</h1>", layout = "<div><% @yield %></div>", name = "Adrian")
HTTP.Messages.Response:
"
HTTP/1.1 200 OK
Content-Type: text/html; charset=utf-8

<html><head></head><body><div><h1>Welcome Adrian</h1>
</div></body></html>"
```
