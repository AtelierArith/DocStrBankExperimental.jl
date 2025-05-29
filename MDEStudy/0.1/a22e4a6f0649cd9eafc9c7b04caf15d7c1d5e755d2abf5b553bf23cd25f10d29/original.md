```
function group_and_reg(
    ds_e::InMemoryDatasets.Dataset,
    data::MarketData,
    f::FormulaTerm
)
```

Calculates a linear regression for the supplied data based on the formula (formula from StatsModels.jl),  therefore, the user needs to know the factor information in the market data.

`group_and_reg` is an intentionally simplistic linear regression.For each firm event, it looks up the  corresponding factors in the firm and market data, and does a regression to calculate the coefficients  of the formular. It also attempts to produce a minimum number of allocations if views of vectors are  passed.

# Arguments

  * `ds_e`:An InMemoryDatasets.Dataset that stores events data
  * `data`: A MarketData structure which stores sorted firm data and market data
  * `f`: A StatsModels.jl formula, provided by user

# Example

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
