```
SeqLogger(
    server_url::AbstractString;
    min_level::Logging.LogLevel=Logging.Info,
    api_key::AbstractString="",
    batch_size::Int=10,
    event_properties...
)
```

`Seq` ログサーバーにログイベントを投稿するためのロガーです。

### 入力

  * `server_url` – `Seq` サーバーの URL (例: `"http://localhost:5341"`)
  * `min_level` – (オプション, `default=Logging.Info`) ログイベントをフィルタリングするための最小ログレベル
  * `api_key` –  (オプション, `default=""`) 登録されたアプリケーション用の API キー文字列
  * `batch_size` – (オプション, `default=10`) 単一の投稿で `Seq` サーバーに送信されるログイベントの数
  * `event_properties` – (オプション) グローバルなログイベントプロパティ

#### グローバルログイベントプロパティ

`SeqLogger` コンストラクタは、キーワード引数を使用してロガーにグローバルなログイベントプロパティを追加することを許可します。

```julia
SeqLogger("http://localhost:5341"; App="DJSON", Env="PROD", Id="24e0d145-d385-424b-b6ec-081aa17d504a")
```

#### ローカルログイベントプロパティ

各個別のログイベントに対して、単一のログイベントにのみ適用される追加のログイベントプロパティを追加できます。

```julia
@info "Log additional user id {userId}" userId="1"
```

注意: これは、[`Logging.current_logger`](@ref) が `SeqLogger` 型であるか、`SeqLogger` を「含む」場合にのみ機能します。
