```
MseedTraceID(this_traceid::MS3TraceID; headers_only=false)
```

`MS3TraceID`オブジェクトから`MseedTraceID`を構築します。これは、`libmseed`の関数の1つを呼び出すことで取得されます。

`headers_only`が`true`の場合、データは読み込まれず、トレース情報のみが読み込まれます。
