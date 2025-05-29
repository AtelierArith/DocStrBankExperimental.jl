```
MseedTraceSegment(T, this_traceseg::MS3TraceSeg; headers_only=false) -> segment
```

`MS3TraceSeg`オブジェクトから`MseedTraceSegment{T}`を構築します。これは`libmseed`の関数のいずれかを呼び出して得られたものです。

`headers_only`が`true`の場合、データはラップされず、`segment`構造体にはヘッダー情報のみが格納されます。
