```
load_amazon_review([path=nothing; category="Electronics"]) -> DataAccessor
```

`path` は特定のカテゴリの [Amazon Reviews Dataset](https://nijianmo.github.io/amazon/index.html) のローカルに保存された小さなセットを指します。各行は (item, user, rating, timestamp) のタプルを持っています。
