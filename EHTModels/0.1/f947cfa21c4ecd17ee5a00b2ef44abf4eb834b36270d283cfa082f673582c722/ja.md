```
visibility_point(model::AbstractModel, u, v, args...)
```

点ごとの可視性を計算する関数です。`visanalytic(::Type{MyModel}) == IsAnalytic()` の場合、これはモデルインターフェースで実装する必要があります。
