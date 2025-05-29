```
html(viewfile::FilePath; layout::Union{Nothing,FilePath} = nothing,
      context::Module = @__MODULE__, status::Int = 200, headers::HTTPHeaders = HTTPHeaders(), vars...) :: HTTP.Response
```

HTML `viewfile`を解析してレンダリングします。オプションで`layout`ファイル内でレンダリングします。有効なファイル形式は`.html.jl`です。

# 引数

  * `viewfile::FilePath`: `Renderer.FilePath`としてのビューファイルへのファイルシステムパス、つまり`Renderer.filepath("/path/to/file.html.jl")`または`path"/path/to/file.html.jl"`
  * `layout::FilePath`: `Renderer.FilePath`としてのレイアウトファイルへのファイルシステムパス、つまり`Renderer.FilePath("/path/to/file.html.jl")`または`path"/path/to/file.html.jl"`
  * `context::Module`: 変数が評価されるモジュール（varsのスコープを提供するため）。通常はコントローラーです。
  * `status::Int`: レスポンスのステータスコード
  * `headers::HTTPHeaders`: HTTPレスポンスヘッダー
