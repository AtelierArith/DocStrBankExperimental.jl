stdlib/Logging/ConsoleLoggerとの違い:

```
- ロギングメッセージのデフォルトのタイムスタンプ（@infoを除く）
- 'shouldlog'関数を渡すことができます。`shouldlog_default`関数は
    HTTP.Serversメッセージおよびmessage_limitsに基づいてフィルタリングします
- :wslog => trueフラグは、'show'メソッドからのコンテキストに応じた出力に使用できます。これは、ユーザーがこのロガーで使用される'show'メソッドを定義できることを意味し、他のモジュールで定義された動作に影響を与えません。
- :limited => trueはデフォルトのIOContextに含まれています。キーワード: show_limited
- string_with_env_wsは特定の型に対して簡単にオーバーロードできるようにエクスポートされています
- @info, @debug, @warnなどは、最初の引数がタプル引数の場合にスプラットします。例えば、

julia> var = "a"
"a"
julia> @info (1, var)
[ Info: 1a
```
