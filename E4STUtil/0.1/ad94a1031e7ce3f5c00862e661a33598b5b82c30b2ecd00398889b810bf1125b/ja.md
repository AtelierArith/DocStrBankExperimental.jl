```
usd_cr(y1, y2; source=gdp, future=nothing) -> r
```

`y1`のUSDから`y2`のUSDへの換算レートを計算します。

オプションのキーワード引数:

  * `source` - `gdp`と`cpi`の間で選択、デフォルトは`gdp`
  * `future` - 想定される将来のインフレ率。次のいずれかにできます:

      * `nothing`（デフォルト） - 範囲外の年が指定された場合にエラーをスロー
      * `rate` - 最大年を超える年のための想定インフレ率、例えば`0.02`は2%のインフレ率を意味します

入力データソース:

  * `gdp` - [bea.gov](https://apps.bea.gov/iTable/iTable.cfm?reqid=19&step=3&isuri=1&1921=survey)からの2021年データで更新、表1.1.9。
  * `cpi` - [bls.gov](https://data.bls.gov/timeseries/CUUR0000SA0)からの2021年データで更新
