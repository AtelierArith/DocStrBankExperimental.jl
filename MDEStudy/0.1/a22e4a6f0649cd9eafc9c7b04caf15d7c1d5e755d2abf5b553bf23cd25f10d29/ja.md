```
function group_and_reg(
    ds_e::InMemoryDatasets.Dataset,
    data::MarketData,
    f::FormulaTerm
)
```

提供されたデータに基づいて線形回帰を計算します。これは、StatsModels.jlからの式に基づいているため、ユーザーは市場データの因子情報を知っている必要があります。

`group_and_reg`は意図的に単純な線形回帰です。各企業のイベントについて、企業データと市場データの対応する因子を検索し、式の係数を計算するために回帰を行います。また、ベクトルのビューが渡された場合、最小限の割り当てを生成しようとします。

# 引数

  * `ds_e`: イベントデータを格納するInMemoryDatasets.Dataset
  * `data`: ソートされた企業データと市場データを格納するMarketData構造体
  * `f`: ユーザーが提供するStatsModels.jlの式

# 例

```@example general
using DLMReader
using MDEStudy
ds_firm = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "firm_ret.csv"), types = Dict(2=>Date)); 
ds_mkt = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "mkt_ret.csv"), types = Dict(1=>Date));
ds_events=filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data","event_dates.csv"),types = Dict(2:6 .=>Date)) |> unique;
mkt_data = MarketData(
ds_mkt,
ds_firm
)
reg_result=group_and_reg(ds_events,data, @formula(ret ~ mkt + smb + hml + umd))
```
