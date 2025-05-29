```
ExchangeMarket
```

Type used for a dictionary of `AssetsPair() => Rate()` pair quotes.

It is given as a Dict{AssetsPair, Rate}, where the keys are the pairs with the base and quote assets and the value is the exchange/trade rate for this pair (i..e. how much in quote units is needed to buy/trande one unit of the base asset).

For instance, the market

```
mkt = ExchangeMarket(AssetsPair("EUR", "USD") => Rate(1.164151))
```

contains the pair `AssetsPair("EUR", "USD")` and the exchange rate `Rate(1.164151)`, which means that one can buy 1 EUR with 1.164151 USD.
