function wdi(indicators::Union{String,Array{String,1}}, countries::Union{String,Array{String,1}}, startyear::Integer=-1, endyear::Integer=-1; extra::Bool=false, sourceid::Integer=2, dflong::Bool=false, verbose::Bool=false)::DataFrame

世界銀行の世界開発指標（WDI）データカタログからデータをダウンロードします。

https://datacatalog.worldbank.org/dataset/world-development-indicators

# 引数

  * `indicators` : 指標名または指標の配列
  * `countries` : ISO 2またはISO 3文字の国コードの文字列または文字列配列、またはすべての国のための`all`。
  * `startyear` : 含める最初の年
  * `endyear` : 含める最後の年（startyearが設定されている場合は必須）
  * `extra` : `true`の場合、追加の国データ（地域、首都、経度、緯度、収入、融資）を含めるべき
  * `sourceid` : ソース番号、詳細は https://api.worldbank.org/v2/sources を参照
  * `dflong` : 長いデータフレーム形式。デフォルトは広い。多くの指標がある場合、`long`の方が扱いやすいかもしれません。
  * `verbose` : `true`の場合、ダウンロードしたURLを印刷

# 例

```julia
df = wdi("SP.POP.TOTL", "US")
df = wdi("SP.POP.TOTL", "US", 1980, 2012)
df = wdi("SP.POP.TOTL", "USA", 1980, 2012, extra=true)
df = wdi("SP.POP.TOTL", "all", 2000, 2000, verbose=true, extra=true)
df = wdi("SP.POP.TOTL", ["US","BR"], 1980, 2012, extra=true)
df = wdi(["SP.POP.TOTL", "NY.GDP.MKTP.CD"], ["US","BR"], 1980, 2012, extra=true)
df = wdi(["SP.POP.TOTL", "NY.GDP.MKTP.CD"], ["US","BR"], 1980, 2012, dflong=true)
```
