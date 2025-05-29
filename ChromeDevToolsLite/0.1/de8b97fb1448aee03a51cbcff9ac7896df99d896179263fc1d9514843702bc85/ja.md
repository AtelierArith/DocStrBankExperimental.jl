```
new_context(
    client::WSClient; viewport::Dict{String, Any} = Dict(), user_agent::String = "")
```

オプションのビューポートとユーザーエージェント設定を使用して新しいブラウザコンテキストを作成します。

注意: Chromeを`--enable-features=NetworkService,NetworkServiceInProcess`で起動する必要があります。

# 例

```julia
client = connect_browser()
context = new_context(client,
    viewport=Dict("width" => 1920, "height" => 1080),
    user_agent="Mozilla/5.0 (iPhone; CPU iPhone OS 14_7_1 like Mac OS X)")
```
