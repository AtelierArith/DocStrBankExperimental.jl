```
ExchangeMarket
```

`AssetsPair() => Rate()` ペアの引用の辞書に使用される型です。

これは Dict{AssetsPair, Rate} として与えられ、キーはベース資産と引用資産のペアであり、値はこのペアの為替/取引レートです（すなわち、ベース資産の1単位を購入/取引するために必要な引用単位の量）。

例えば、市場

```
mkt = ExchangeMarket(AssetsPair("EUR", "USD") => Rate(1.164151))
```

はペア `AssetsPair("EUR", "USD")` と為替レート `Rate(1.164151)` を含んでおり、これは1 EURを1.164151 USDで購入できることを意味します。
