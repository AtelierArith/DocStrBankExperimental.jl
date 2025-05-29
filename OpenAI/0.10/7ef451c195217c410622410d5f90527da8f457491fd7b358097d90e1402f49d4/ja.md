```
アシスタントの更新
```

assistants = list*assistants(     api*key,     limit=2,     )

# 引数

  * `api_key::String`: OpenAI APIキー
  * `assistant_id::String`: アシスタントID（例："asst_i1MDikQGNk2PJGtltQljCI6X"）

# キーワード引数

  * `model_id::String`: オプション。アシスタントに使用するモデルID。
  * `name::String`: オプション。アシスタントの名前。
  * `description::String`: オプション。アシスタントの説明。
  * `instructions::String`: オプション。アシスタントの指示。
  * `tools::Vector`: オプション。アシスタントのためのツール。`code_interpreter`、`retrieval`、または`function`を含むことができます。
  * `file_ids::Vector`: オプション。アシスタントに添付されているファイルID。
  * `metadata::Dict`: オプション。アシスタントのメタデータ。主に記録保持のために使用されます。メタデータには最大16のキーと値のペアを含めることができます。キーは最大64文字、値は最大512文字までです。
  * `http_kwargs::NamedTuple`: オプション。HTTP.requestに渡すキーワード引数。

エンドポイントの詳細については、[https://platform.openai.com/docs/api-reference/assistants/modifyAssistant](https://platform.openai.com/docs/api-reference/assistants/modifyAssistant)を訪れてください。

# 使用法

```julia
assistant = modify_assistant(
    api_key,
    "asst_i1MDikQGNk2PJGtltQljCI6X",
    name="My Assistant, renamed",
)
```

は次のような結果を返すべきです。

```
Main.OpenAI.OpenAIResponse{JSON3.Object{Vector{UInt8}, Vector{UInt64}}}(200, {
             "id": "asst_i1MDikQGNk2PJGtltQljCI6X",
         "object": "assistant",
     "created_at": 1701360630,
           "name": "My Assistant, renamed",
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
