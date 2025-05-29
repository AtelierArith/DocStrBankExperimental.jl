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

# Arguments

  * `ds_market`: An InMemoryDatasets.Dataset that stores market data, indexed by date.   The dates must be a unique set. The column name for the date column is specified   by the keyword argument "date*col*market"
  * `ds_firms`: An InMemoryDatasets.Dataset that stores firm data. Each firm must have a   unique set of dates. The column name for the date column is specified   by the keyword argument "date*col*firms" and the firm ID column is specified   by the keyword argument "id_col"
  * `valuecols_market=nothing`: If left as nothing, all other columns in `ds_market` are   used as the value columns. These are the columns that are stored in the resulting   dataset. Otherwise a vector of Symbol or String specifying column names.
  * `valuecols_firms=nothing`: Same as above
  * `id_col=firm_id`: The column corresponding to the set of firm IDs in `ds_firms`

MarketData is the main data storage structure. Data is stored for each firm in a Dataset and left joined with market data by ":date" column, and the market data itself  is changed to a NamedTuple (names corresponding to column names, such as "ret"), and the keys  for the Dict corresponding to market factor.

Any firm data must have a corresponding market data date, so there cannot be a firm return if there is not a market return on that date.

# Example

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
