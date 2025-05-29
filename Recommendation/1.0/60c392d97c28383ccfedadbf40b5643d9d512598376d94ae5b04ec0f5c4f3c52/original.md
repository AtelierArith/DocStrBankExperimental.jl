```
load_amazon_review([path=nothing; category="Electronics"]) -> DataAccessor
```

`path` points to a locally saved small set of [Amazon Reviews Dataset](https://nijianmo.github.io/amazon/index.html) for a particular category. Each row has a tuple of (item, user, rating, timestamp).
