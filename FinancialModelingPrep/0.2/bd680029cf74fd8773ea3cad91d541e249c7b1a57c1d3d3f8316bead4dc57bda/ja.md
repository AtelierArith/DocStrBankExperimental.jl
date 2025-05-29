```
price_quotes(fmp, market)
```

指定された市場の価格見積もりを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `market::String`: 金融市場。

詳細については、[Stock-Quote](https://site.financialmodelingprep.com/developer/docs/#Stock-Price)を参照してください。 詳細については、[Index-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-majors-indexes-(Dow-Jones%2C-Nasdaq%2C-S&P-500))を参照してください。 詳細については、[Euronext-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-EuroNext)を参照してください。 詳細については、[TSX-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-TSX)を参照してください。 詳細については、[Crypto-Quote](https://site.financialmodelingprep.com/developer/docs/#Cryptocurrencies)を参照してください。 詳細については、[Forex-Quote](https://site.financialmodelingprep.com/developer/docs/#Forex-(FX))を参照してください。 詳細については、[Commodity-Quote](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-Major-Commodities-(Gold%2C-Silver%2C-Oil))を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 主要なインデックスの価格見積もりを取得
data = price_quote(fmp, "index")

# NYSEの価格見積もりを取得
data = price_quote(fmp, "nyse")

# TSXの価格見積もりを取得
data = price_quote(fmp, "euronext")

# euronextの価格見積もりを取得
data = price_quote(fmp, "tsx")

# 暗号の価格見積もりを取得
data = price_quote(fmp, "crypto")

# 外国為替の価格見積もりを取得
data = price_quote(fmp, "forex")

# 商品の価格見積もりを取得
data = price_quote(fmp, "commodity")
```
