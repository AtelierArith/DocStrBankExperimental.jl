executive*compensation*benchmarks(fmp, year)

指定された年の役員報酬ベンチマークを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `year::Integer`: カレンダー年。

詳細については、[Executive-Compensation](https://site.financialmodelingprep.com/developer/docs/#Executive-Compensation)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2020年の役員報酬ベンチマークを取得
data = executive_compensation_benchmarks(fmp, year = 2020)
```
