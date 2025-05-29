```
MseedTraceList(mstl::Ref{Ptr{MS3TraceList}}; headers_only=false)
```

`MS3TraceList`構造体への参照から`MseedTraceList`を構築します。これは`libmseed`の関数のいずれかを呼び出して取得したものです。

この関数は完全な`MseedTraceList`を構築し、`mstl`からデータをコピーします。ただし、`headers_only`が`true`の場合はデータはコピーされません。
