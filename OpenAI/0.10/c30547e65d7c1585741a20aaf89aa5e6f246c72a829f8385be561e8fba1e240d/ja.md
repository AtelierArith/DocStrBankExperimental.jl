```
アシスタントのリスト
```

`created_at` タイムスタンプでソートされたアシスタントのリストを含む `OpenAIResponse` オブジェクトを返します。

# 引数:

  * `api_key::String`: OpenAI API キー

# キーワード引数:

  * `limit::Integer` (オプション): 返すアシスタントの最大数。デフォルトは 20 で、1 から 100 の間でなければなりません。
  * `order::String` (オプション): アシスタントをリストする順序。`asc` または `desc` である可能性があります。デフォルトは `desc`（最新が最初）。
  * `after` (オプション): ページネーションで使用するカーソル。`after` はリスト内の位置を定義するオブジェクト ID です。たとえば、リストリクエストを行い、100 のオブジェクトを受け取り、`obj_foo` で終了した場合、次の呼び出しには `after=obj_foo` を含めてリストの次のページを取得できます。
  * `before` (オプション): ページネーションで使用するカーソル。`before` はリスト内の位置を定義するオブジェクト ID です。たとえば、リストリクエストを行い、100 のオブジェクトを受け取り、`obj_bar` で始まった場合、次の呼び出しには `before=obj_bar` を含めてリストの前のページを取得できます。
  * `http_kwargs::NamedTuple`: オプション。HTTP.request に渡すキーワード引数。

エンドポイントの詳細については、[https://platform.openai.com/docs/api-reference/assistants/listAssistants](https://platform.openai.com/docs/api-reference/assistants/listAssistants) を訪問してください。

# 使用法

```julia
assistants = list_assistants(
    api_key,
    limit=2,
)
```

は次のようなものを返すべきです。

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
     "object": "list",
       "data": [
                 {
                              "id": "asst_i1MDikQGNk2PJGtltQljCI6X",
                          "object": "assistant",
                      "created_at": 1701360630,
                            "name": "My Assistant",
                     "description": "My first assistant",
                           "model": "gpt-3.5-turbo-1106",
                    "instructions": "This is my first assistant",
                           "tools": [],
                        "file_ids": [],
                        "metadata": {
                                       "key2": "value2",
                                       "key1": "value1"
                                    }
                 }
               ],
   "first_id": "asst_i1MDikQGNk2PJGtltQljCI6X",
    "last_id": "asst_i1MDikQGNk2PJGtltQljCI6X",
   "has_more": false
})
```
