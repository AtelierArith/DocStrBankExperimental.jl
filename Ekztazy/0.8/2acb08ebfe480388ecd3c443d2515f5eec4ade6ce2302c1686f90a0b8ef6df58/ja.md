```
Client(
    token::String
    application_id::Snowflake
    intents::Int;
    presence::Union{Dict, NamedTuple}=Dict(),
    strategies::Dict{DataType, <:CacheStrategy}=Dict(),
    version::Int=9,
) -> Client
```

Discordボット。`Client`はゲートウェイに接続し、イベントに応答し、メッセージの送信/削除、ユーザーのキック/バンなどのアクションを実行するためにREST API呼び出しを行うことができます。

### ボットトークン

ボットトークンは、新しいアプリケーションを作成することで取得できます [here](https://discordapp.com/developers/applications)。トークンをJuliaコードにハードコーディングしないようにしてください！代わりに環境変数または設定ファイルを使用してください。

### アプリケーションID

ボットのアプリケーションIDは [here](https://discordapp.com/developers/applications) で見つけることができます。アプリケーションIDをJuliaコードにハードコーディングしないようにしてください！代わりに環境変数または設定ファイルを使用してください。

### インテント

インテントを表す整数。詳細は [here](https://discord.com/developers/docs/topics/gateway#gateway-intents) を参照してください。

### プレゼンス

`presence`キーワードは接続時にボットのプレゼンスを設定します。また、将来の[`set_game`](@ref)呼び出しのデフォルトも設定します。スキーマは [here](https://discordapp.com/developers/docs/topics/gateway#update-status-gateway-status-update-structure) に従う必要があります。

### キャッシュ制御

デフォルトでは、Discordからのほとんどのデータは後で使用するためにキャッシュされます。ただし、メモリリークを避けるために、すべてのデータが永遠に保持されるわけではありません。デフォルトの設定は、[`Message`](@ref)を除いてすべてを保持し、これらは6時間後に削除されます。デフォルトの設定はほとんどのワークロードに対して十分ですが、`strategies`キーワードを使用してタイプごとに独自の戦略を指定できます。キーは次のいずれかであることができます：

  * [`Guild`](@ref)
  * [`DiscordChannel`](@ref)
  * [`Message`](@ref)
  * [`User`](@ref)
  * [`Member`](@ref)
  * [`Presence`](@ref)

潜在的な値については、[`CacheStrategy`](@ref)を参照してください。

キャッシュは、[`enable_cache!`](@ref)および[`disable_cache!`](@ref)を使用して、全体を永続的または一時的に無効化/有効化することもできます。

### APIバージョン

`version`キーワードは使用するDiscord APIのバージョンを選択します。`9`以外のものを使用することは、Ekztazy.jlの開発者によって公式にサポートされていません。

### シャーディング

シャーディングは自動的に処理されます。利用可能なプロセスの数は、作成されるシャードの数です。詳細については、[シャーディングの例](https://github.com/Xh4H/Discord.jl/blob/master/examples/sharding.jl)を参照してください。
