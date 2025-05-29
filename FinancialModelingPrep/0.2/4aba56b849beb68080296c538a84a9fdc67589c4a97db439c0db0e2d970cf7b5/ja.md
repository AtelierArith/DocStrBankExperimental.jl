```
delisted_companies(fmp, params...)
```

上場廃止企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Delisted-Companies](https://site.financialmodelingprep.com/developer/docs/#Delisted-Companies)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 上場廃止企業の最初のページを取得
data = delisted_companies(fmp, page = 0)
```
