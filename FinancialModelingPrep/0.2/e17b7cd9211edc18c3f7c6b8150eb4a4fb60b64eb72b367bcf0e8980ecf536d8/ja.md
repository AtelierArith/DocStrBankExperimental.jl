```
most_active(fmp)
```

最もアクティブなシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については、[Most-Active](https://site.financialmodelingprep.com/developer/docs/#Most-Active-Stock-Companies)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 最もアクティブなシンボルを取得
data = most_active(fmp)
```
