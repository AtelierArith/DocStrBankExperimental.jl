```
upgrades_and_downgrades_by_company(fmp, company)
```

指定された会社のアップグレードとダウングレードを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Upgrades-&-Downgrades-By-Company](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-By-Company)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# バークレイズのアップグレードとダウングレードのコンセンサスを取得
data = upgrades_and_downgrades_by_company(fmp, company = "Barclays")
```
