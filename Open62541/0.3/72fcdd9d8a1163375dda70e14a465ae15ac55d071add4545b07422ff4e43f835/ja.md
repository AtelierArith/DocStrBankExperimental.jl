```
UA_Server_call(server::Ptr{UA_Server}, request::Ptr{UA_CallMethodRequest}, result::Ptr{UA_CallMethodResult})::Nothing
```

は、サーバーAPIを使用して、`server`上のメソッド呼び出しリクエスト`request`を処理します。`result`が変更されることに注意してください。
