```
LanguageServerInstance(pipe_in, pipe_out, env="", depot="", err_handler=nothing, symserver_store_path=nothing)
```

言語サーバーのインスタンスを構築します。

インスタンスが `run` されると、`pipe_out` から JSON-RPC を読み取り、`pipe_in` に JSON-RPC を書き込みます。これは [言語サーバー仕様](https://microsoft.github.io/language-server-protocol/specifications/specification-3-14/) に従います。通常の使用では、言語サーバーは `LanguageServerInstance(stdin, stdout, false, "/path/to/environment")` でインスタンス化できます。

# 引数

  * `pipe_in::IO`: JSON-RPC を読み取るためのパイプ。
  * `pipe_out::IO`: JSON-RPC を書き込むためのパイプ。
  * `env::String`: 言語サーバーが実行されている [環境](https://docs.julialang.org/en/v1.2/manual/code-loading/#Environments-1) へのパス。空の文字列は Julia のデフォルト環境を使用します。
  * `depot::String`: 言語サーバーが `env` で必要なパッケージを探す [`JULIA_DEPOT_PATH`](https://docs.julialang.org/en/v1.2/manual/environment-variables/#JULIA_DEPOT_PATH-1) を設定します。
  * `err_handler::Union{Nothing,Function}`: `nothing` でない場合、すべてのエラーをキャッチし、`err_handler(err, bt)` というシグネチャを持つエラーハンドラ関数に渡します。主に VS Code のクラッシュレポート実装で使用されます。
  * `symserver_store_path::Union{Nothing,String}`: `nothing` が渡された場合、シンボルサーバーのキャッシュはパッケージ内のフォルダーに保存されます。絶対パスが渡された場合、シンボルサーバーはそのパスにキャッシュファイルを保存します。呼び出す前に、そのパスはディスク上に存在している必要があります。
