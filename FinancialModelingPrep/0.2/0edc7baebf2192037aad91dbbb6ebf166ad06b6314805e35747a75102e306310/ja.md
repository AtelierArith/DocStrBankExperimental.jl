```
cik_from_insider(fmp, name)
```

指定されたインサイダー名に一致するすべてのCIKを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `name::String`: 名前。

詳細については[CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# "zuckerberg mark"に一致するすべてのCIKを取得
data = cik_from_insider(fmp, "zuckerberg%20mark")
```
