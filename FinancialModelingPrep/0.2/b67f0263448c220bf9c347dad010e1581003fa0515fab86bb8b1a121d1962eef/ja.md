```
income_statements_growth(fmp, symbol, params...)
```

指定されたシンボルの収益計算書の成長を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Income-Statements-Growth](https://site.financialmodelingprep.com/developer/docs/#Financial-Statements-Growth)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の過去 5 年間の収益計算書の成長を取得
data = income_statements_growth(fmp, "AAPL", limit = 5)
```
