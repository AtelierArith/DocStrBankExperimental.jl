```
company_outlook(fmp, symbol, accessor)
```

指定されたシンボルの企業の見通しのJSONテーブルまたは辞書を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `accessor::Symbol`: ネストされた配列を含むアクセサーシンボル。

詳細については、[Company-Outlook](https://site.financialmodelingprep.com/developer/docs/#Company-Outlook)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの企業の見通しを取得
data = company_outlook(fmp, "AAPL")
```
