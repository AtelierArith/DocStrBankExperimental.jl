```
earnings_call_transcripts(fmp, symbol)
earnings_call_transcripts(fmp, symbol, year)
earnings_call_transcripts(fmp, symbol, year, quarter)
```

指定されたシンボルのための決算発表のトランスクリプトを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル、または指定しない場合は「all」。
  * `year::Integer`: カレンダー年。
  * `quarter::Integer`: 1、2、3、または4のいずれか。

詳細については、[Earnings-Call-Transcript](https://site.financialmodelingprep.com/developer/docs/#Earning-Call-Transcript)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの利用可能なトランスクリプト日を取得
data = earnings_call_transcripts(fmp, "AAPL")

# 2022年のQ3におけるAAPLの決算発表トランスクリプトを取得
data = earnings_call_transcripts(fmp, "AAPL", year = 2022, quarter = 3)
```
