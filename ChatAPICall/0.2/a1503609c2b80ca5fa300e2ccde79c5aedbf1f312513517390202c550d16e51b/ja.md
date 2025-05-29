```
ErrResp
```

OpenAI APIからのエラー応答。

# フィールド

  * `message::String`: エラーメッセージ。
  * `type::String`: エラータイプ。
  * `param::Union{Nothing, String}`: エラーを引き起こしたパラメータ。
  * `code::String`: エラーコード。
