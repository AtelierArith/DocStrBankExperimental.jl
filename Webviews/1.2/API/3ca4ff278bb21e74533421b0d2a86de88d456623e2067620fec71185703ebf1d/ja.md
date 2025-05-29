```
return_raw(w::Webview, seq::String, success::Bool, result_or_err)
```

ネイティブバインディングから値を返すことを可能にします。元のリクエストポインタを提供する必要があり、内部RPCエンジンがリクエストとレスポンスを一致させるのに役立ちます。
