```
アシスタントを取得
```

特定のアシスタントのための `OpenAIResponse` オブジェクトを返します。

# 引数:

  * `api_key::String`: OpenAI API キー
  * `assistant_id::String`: アシスタント ID (例: "asst_i1MDikQGNk2PJGtltQljCI6X")

# キーワード引数:

  * `http_kwargs::NamedTuple`: オプション。HTTP.request に渡すキーワード引数。

エンドポイントの詳細については、[https://platform.openai.com/docs/api-reference/assistants/getAssistant](https://platform.openai.com/docs/api-reference/assistants/getAssistant) を訪問してください。

# 使用法

```julia
assistant = get_assistant(
    api_key,
    "asst_i1MDikQGNk2PJGtltQljCI6X"
)
```

は次のようなものを返すべきです

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
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
})
```
