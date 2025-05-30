```
load_amazon_review([path=nothing; category="Electronics"]) -> DataAccessor
```

`path` は特定のカテゴリのローカルに保存された小さなセットの [Amazon Reviews Dataset](https://nijianmo.github.io/amazon/index.html) を指します。各行には (item, user, rating, timestamp) のタプルがあります。
