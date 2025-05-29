```
sector_pe_ratios(fmp, params...)
```

セクターのPE比率を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Sectors-PE-Ratio](https://site.financialmodelingprep.com/developer/docs/#Sectors-PE-Ratio)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2023年1月1日のNYSEのセクターPE比率を取得
data = sector_pe_ratios(fmp, date = "2023-01-01", exchange = "NYSE")
```
