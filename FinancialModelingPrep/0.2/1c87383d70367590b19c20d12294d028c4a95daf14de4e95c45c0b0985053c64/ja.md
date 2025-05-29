```
sec_filings(fmp, symbol, params...)
```

指定されたシンボルのSEC提出書類を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル、または指定しない場合は「all」。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については[SEC-Filings](https://site.financialmodelingprep.com/developer/docs/#SEC-Filings)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの10-K提出書類の最初のページを取得
data = sec_filings(fmp, "AAPL", type = "10-K", page = 0)
```
