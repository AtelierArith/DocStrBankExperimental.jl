```
load(server::Server, j::Job)
```

`server`の`j.dir`にある[`Job`](@ref)をロードしようとします。正確に一致するディレクトリが見つからない場合、`j.dir`を構成するジョブディレクトリのリストが返されます。
