```
info::UnionSplitApplyCallInfo <: CallInfo
```

`UnionSplitInfo`と同様ですが、`MethodMatchInfo`ではなく`ApplyCallInfo`用です。この情報は、`_apply_iterate`呼び出しでない任意のステートメントでは不正です。
