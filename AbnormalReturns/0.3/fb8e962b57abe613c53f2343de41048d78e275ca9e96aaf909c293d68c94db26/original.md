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

## Arguments

  * `df_market`: A Tables.jl compatible source that stores market data, indexed by date.   The dates must be a unique set. The column name for the date column is specified   by the keyword argument "date*col*market"
  * `df_firms`: A Tables.jl compatible source that stores firm data. Each firm must have a   unique set of dates. The column name for the date column is specified   by the keyword argument "date*col*firms" and the firm ID column is specified   by the keyword argument "id_col"
  * `valuecols_market=nothing`: If left as nothing, all other columns in `df_market` are   used as the value columns. These are the columns that are stored in the resulting   dataset. Otherwise a vector of Symbol or String specifying column names.
  * `valuecols_firms=nothing`: Same as above
  * `id_col=:permno`: The column corresponding to the set of firm IDs in `df_firms`
  * `add_intercept_col=true`: Whether to add a column to the data for an intercept (which is   always equal to 1)

MarketData is the main data storage structure. Data is stored for each firm in a Dict, where the data itself is a NamedTuple (names corresponding to column names, such as "ret"), and the keys for the Dict corresponding to firm IDs. The MarketData struct also stores overall market data and a calendar of dates.

Any firm data must have a corresponding market data date, so there cannot be a firm return if there is not a market return on that date.

## Example

```@example general
df_firm = CSV.File(joinpath(data_dir, "daily_ret.csv"))
df_mkt = CSV.File(joinpath(data_dir, "mkt_ret.csv"))
df_mkt[!, :mkt] = df_mkt.mktrf .+ df_mkt.rf
mkt_data = MarketData(
    df_mkt,
    df_firm
)
```
