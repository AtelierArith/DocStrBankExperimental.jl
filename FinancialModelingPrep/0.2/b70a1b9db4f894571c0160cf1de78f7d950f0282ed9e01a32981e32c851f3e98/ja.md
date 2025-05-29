```
industry_pe_ratios(fmp, params...)
```

業界のPE比率を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Industries-PE-Ratio](https://site.financialmodelingprep.com/developer/docs/#Industries-PE-Ratio)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2023年1月1日のNYSEの業界PE比率を取得
data = industry_pe_ratios(fmp, date = "2023-01-01", exchange = "NYSE")
```
