```
FMP(apikey, baseurl, headers)
```

APIサーバーのエンドポイントと対話するためのFinancial Modeling Prepインスタンスを作成します。

# 引数

  * `apikey::String` = `"demo"`
  * `baseurl::String` = `"https://financialmodelingprep.com"`
  * `headers::Dict{String, String}` = `Dict("Upgrade-Insecure-Requests" => "1")`

# 例

```julia
# あなたのFMP APIキーをロードする
FMP_API_KEY = ENV("FMP_API_KEY")

# APIキーを名前で渡して新しいFMPインスタンスを作成する
fmp = FMP(apikey = FMP_API_KEY)
```
