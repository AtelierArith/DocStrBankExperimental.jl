```
owntime([stacktraces]; stackframe_filter, warn_on_full_buffer=true)
```

各 `StackFrame` に費やされた時間をカウントしますが、そのサブコールは *除外* されます。

提供された場合、`stackframe_filter` は単一の `StackFrame` を受け取り、カウントに含めるべきであれば `true` を返す関数である必要があります。

より高度なフィルタリングは、`OwnTime.stacktraces()` から `StackTrace`s を前処理し、その後これらの `StackTrace`s をこの関数に渡すことで行うことができます。

参照: [`OwnTime.stacktraces`](@ref) [`StackTraces.StackFrame`](@ref)
