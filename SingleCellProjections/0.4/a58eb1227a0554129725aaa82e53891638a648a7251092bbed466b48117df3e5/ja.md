```
project(data::DataMatrix, models, args...; verbose=true, kwargs...)
```

複数の `models` への射影のための便利な関数です。基本的には `foldl` を呼び出し、いくつかの `@info` メッセージを表示します（`verbose=true` の場合）。ほとんどの場合、このメソッドを直接使用するのではなく、`project(data, base::DataMatrix)` を呼び出す方が良いです。
