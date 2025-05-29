```
insiders_list(fmp, params...)
```

指定されたパラメータに一致するすべてのインサイダーの名前とそのCIKを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# ページ3からすべてのインサイダーの名前とそのCIKを取得
data = insiders_list(fmp, page = 3)
```
