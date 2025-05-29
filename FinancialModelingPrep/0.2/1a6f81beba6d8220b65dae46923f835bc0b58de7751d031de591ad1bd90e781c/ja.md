```
forms_13f(fmp, cik, date)
```

指定されたCIKと日付に一致するすべてのフォーム13F提出を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。
  * `date::String`: yyyy-mm-dd形式の日付文字列。

詳細については、[Form-13F](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2022年6月30日のCIKのすべてのフォーム13Fを取得します。
data = forms_13f(fmp, cik = "0001067983", date = "2022-06-30")
```
