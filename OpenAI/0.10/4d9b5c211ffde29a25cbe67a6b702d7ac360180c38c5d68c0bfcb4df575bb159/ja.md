```
スレッドを作成

POST https://api.openai.com/v1/threads
```

# 引数:

  * `api_key::String`: OpenAI APIキー
  * `messages::Vector`: スレッドを作成するためのメッセージのリスト。メッセージは以下のフィールドを持つ辞書です:

      * `role`: メッセージの役割。現在は `user` のみがサポートされています。
      * `content`: メッセージの内容。
      * `file_ids`: オプション。メッセージに添付するファイルIDのリスト。
      * `metadata`: オプション。メッセージのメタデータ。

# キーワード引数:

  * `http_kwargs::NamedTuple`: オプション。HTTP.requestに渡すキーワード引数。

# 使用法

```julia
thread_id = create_thread(api_key, [
    Dict("role" => "user", "content" => "こんにちは、元気ですか？")
]).response.id
```
