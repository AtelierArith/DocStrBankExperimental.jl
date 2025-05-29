```
struct MarketData
    calendar::MarketCalendar
    firmdata::InMemoryDatasets.Dataset
    marketdata::NamedTuple
end
```

# Example

```@setup general
using DLMReader
using MDEStudy
ds_firm = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "firm_ret.csv"), types = Dict(2=>Date)); 
ds_mkt = filereader(joinpath(pathof(MDEStudy),"..","..","benchmark","data", "mkt_ret.csv"), types = Dict(1=>Date));
mkt_data = MarketData(
ds_mkt,
ds_firm
)
```
