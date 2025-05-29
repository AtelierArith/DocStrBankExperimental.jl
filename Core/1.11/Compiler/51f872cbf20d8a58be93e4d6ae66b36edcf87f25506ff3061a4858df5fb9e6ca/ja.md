```
info::ApplyCallInfo <: CallInfo
```

この情報は、`_apply_iterate(...)` の任意の呼び出しに適用され、適用される実際の呼び出しの情報と、`iterate` 関数への暗黙の呼び出しの情報の両方をキャプチャします。呼び出し自体が別の `_apply_iterate` である可能性があることに注意してください。この場合、`info.call` フィールドは別の `ApplyCallInfo` になります。この情報は、`_apply_iterate` 呼び出しでない任意のステートメントでは不正です。
