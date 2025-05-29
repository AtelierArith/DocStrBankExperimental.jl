```
historical_sector_performances(fmp, params...)
```

過去のセクターのパフォーマンスを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Sectors-Performance](https://site.financialmodelingprep.com/developer/docs/#Stock-Market-Sectors-Performance)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 10件の最新の過去のセクターのパフォーマンスを取得
data = historical_sector_performances(fmp, limit = 10)
```
