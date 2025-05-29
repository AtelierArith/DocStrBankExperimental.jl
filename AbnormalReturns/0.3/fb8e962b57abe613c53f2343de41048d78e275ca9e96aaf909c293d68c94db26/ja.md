```
function MarketData(
    df_market,
    df_firms;
    date_col_market=:date,
    date_col_firms=:date,
    id_col=:permno,
    add_intercept_col=true,
    valuecols_market=nothing,
    valuecols_firms=nothing
)
```

## 引数

  * `df_market`: 日付でインデックスされた市場データを格納する、Tables.jl 互換のソース。日付は一意のセットでなければなりません。日付列の列名はキーワード引数 "date*col*market" で指定されます。
  * `df_firms`: 企業データを格納する、Tables.jl 互換のソース。各企業は一意の日付セットを持っている必要があります。日付列の列名はキーワード引数 "date*col*firms" で指定され、企業ID列はキーワード引数 "id_col" で指定されます。
  * `valuecols_market=nothing`: 何も指定しない場合、`df_market` の他のすべての列が値列として使用されます。これらは結果のデータセットに格納される列です。そうでない場合は、列名を指定する Symbol または String のベクターです。
  * `valuecols_firms=nothing`: 上記と同じです。
  * `id_col=:permno`: `df_firms` における企業IDのセットに対応する列。
  * `add_intercept_col=true`: データにインターセプト用の列を追加するかどうか（常に1に等しい）。

MarketData は主要なデータストレージ構造です。データは各企業ごとに Dict に格納され、データ自体は NamedTuple（名前は列名に対応、例えば "ret"）であり、Dict のキーは企業IDに対応します。MarketData 構造体は全体の市場データと日付のカレンダーも格納します。

任意の企業データは対応する市場データの日付を持っている必要があるため、その日付に市場リターンがない場合、企業リターンは存在できません。

## 例

```@example general
df_firm = CSV.File(joinpath(data_dir, "daily_ret.csv"))
df_mkt = CSV.File(joinpath(data_dir, "mkt_ret.csv"))
df_mkt[!, :mkt] = df_mkt.mktrf .+ df_mkt.rf
mkt_data = MarketData(
    df_mkt,
    df_firm
)
```
