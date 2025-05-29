```
RankerModel
```

パッセージをランク付けするためのモデルで、エンコーダーと推論のためのONNXセッションを含みます。

ランク付けには、`rank(ranker, query, passages)`として、またはファンクタとして`ranker(query, passages)`として使用します。
