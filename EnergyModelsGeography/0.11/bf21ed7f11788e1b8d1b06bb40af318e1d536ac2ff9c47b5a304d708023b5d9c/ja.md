```
exchange_limit(a::LimitedExchangeArea)
exchange_limit(a::LimitedExchangeArea, p::Resource)
exchange_limit(a::LimitedExchangeArea, p::Resource, t)
```

エリア `a` における交換リソースの制限を辞書として返します。リソース `p` の値は `TimeProfile` として、または運用期間 `t` におけるリソース `p` の値として返されます。

リソース `p` が含まれていない場合、関数は `FixedProfile(0)` または値 0 を返します。
