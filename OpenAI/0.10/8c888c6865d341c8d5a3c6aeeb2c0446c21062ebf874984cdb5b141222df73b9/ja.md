```
アシスタントをIDで削除します。

# 引数:

  * `api_key::String`: OpenAI APIキー
  * `assistant_id::String`: アシスタントID（例: "asst_i1MDikQGNk2PJGtltQljCI6X"）

# キーワード引数:

  * `http_kwargs::NamedTuple`: オプション。HTTP.requestに渡すキーワード引数。

エンドポイントの詳細については、[https://platform.openai.com/docs/api-reference/assistants/deleteAssistant](https://platform.openai.com/docs/api-reference/assistants/deleteAssistant)を参照してください。

# 使用法

```

julia

# 削除するアシスタントを作成

resp = create*assistant(     api*key,     "gpt-3.5-turbo-1106",     name="My Assistant", ) resp_id = resp.response.id

# そのアシスタントを削除

delete*assistant(     api*key,     resp_id, )

```

次のような結果が返されるはずです。

```

Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {         "id": "asst_15GkSjSnF5SzGpItO22L6JYI",     "object": "assistant.deleted",    "deleted": true }) ```
