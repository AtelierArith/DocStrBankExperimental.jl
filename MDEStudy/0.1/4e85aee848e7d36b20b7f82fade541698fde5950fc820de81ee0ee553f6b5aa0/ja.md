```
function MarketData(
    ds_market::InMemoryDatasets.Dataset,
    ds_firms::InMemoryDatasets.Dataset;
    date_col_market=:date,
    date_col_firms=:date,
    id_col=:firm_id,
    valuecols_market=nothing,
    valuecols_firms=nothing
)
```

# 引数

  * `ds_market`: 日付でインデックスされた市場データを格納する InMemoryDatasets.Dataset。日付は一意のセットでなければなりません。日付列の列名はキーワード引数 "date*col*market" で指定されます。
  * `ds_firms`: 企業データを格納する InMemoryDatasets.Dataset。各企業は一意の日付セットを持たなければなりません。日付列の列名はキーワード引数 "date*col*firms" で指定され、企業ID列はキーワード引数 "id_col" で指定されます。
  * `valuecols_market=nothing`: 何も指定しない場合、`ds_market` の他のすべての列が値列として使用されます。これらは結果のデータセットに格納される列です。そうでない場合は、列名を指定する Symbol または String のベクターです。
  * `valuecols_firms=nothing`: 上記と同じです。
  * `id_col=firm_id`: `ds_firms` における企業IDのセットに対応する列です。

MarketData は主要なデータストレージ構造です。データは各企業の Dataset に格納され、":date" 列で市場データと左結合され、市場データ自体は NamedTuple に変更され（名前は "ret" などの列名に対応）、市場ファクターに対応する Dict のキーとなります。

すべての企業データは対応する市場データの日付を持たなければならないため、その日付に市場リターンがない場合、企業リターンは存在できません。

# 例

```@example general
using DLMReader
using MDEStudy
ds_firm = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "firm_ret.csv"), types = Dict(2=>Date)); 
ds_mkt = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "mkt_ret.csv"), types = Dict(1=>Date));
mkt_data = MarketData(
ds_mkt,
ds_firm
)
```
