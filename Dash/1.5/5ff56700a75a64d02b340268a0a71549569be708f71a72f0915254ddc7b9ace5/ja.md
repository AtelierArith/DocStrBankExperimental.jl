```
run_server(app::DashApp, host = HTTP.Sockets.localhost, port = 8050; debug::Bool = false)
```

Dashサーバーを実行する

# 引数

  * `app` - Dashアプリケーション
  * `host` - ホスト
  * `port` - ポート
  * `debug::Bool = false` - すべての開発ツールを有効/無効にする

# 例

```jldoctest
julia> app = dash() do
    html_div() do
        html_h1("テストダッシュボード")
    end
end
julia>
julia> run_server(handler,  HTTP.Sockets.localhost, 8050)
```
