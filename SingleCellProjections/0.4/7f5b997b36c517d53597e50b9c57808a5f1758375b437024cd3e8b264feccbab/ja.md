```
project(data::DataMatrix, model::ProjectionModel, args...; verbose=true, kwargs...)
```

コアプロジェクション関数。単一の`ProjectionModel` `model`に基づいて`data`をプロジェクトします。ほとんどの場合、このメソッドを直接使用するのではなく、`project(data, base::DataMatrix)`を呼び出す方が良いです。
