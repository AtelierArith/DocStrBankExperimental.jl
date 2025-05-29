```
internalrequest(req::HTTP.Request; middleware::Vector=[], serialize::Bool=true, catch_errors::Bool=true)
```

ルーターに登録された他のエンドポイントの1つを直接呼び出し、独自のミドルウェアを使用して、グローバルに定義されたミドルウェアをバイパスします。
