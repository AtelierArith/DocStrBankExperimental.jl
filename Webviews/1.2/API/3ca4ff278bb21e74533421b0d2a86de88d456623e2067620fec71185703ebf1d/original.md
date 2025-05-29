```
return_raw(w::Webview, seq::String, success::Bool, result_or_err)
```

Allows to return a value from the native binding. Original request pointer must be provided to help internal RPC engine match requests with responses.
