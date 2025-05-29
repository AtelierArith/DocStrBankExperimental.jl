```
esg_score_benchmarks(fmp, year)
```

指定されたシンボルのESGスコアベンチマークを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `year::Integer`: カレンダー年。

詳細については、[ESG-Benchmarking](https://site.financialmodelingprep.com/developer/docs/#ESG-Benchmarking-By-Sector-and-Year)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2023年のESGスコアベンチマークを取得
data = esg_score_benchmarks(fmp, year = 2023)
```
