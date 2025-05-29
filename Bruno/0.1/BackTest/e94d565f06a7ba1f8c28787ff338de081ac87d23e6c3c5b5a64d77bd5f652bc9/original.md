```
strategy_returns(
    objs::Vector{<:FinancialInstrument},
    pricing_model,
    strategy_type,
    future_prices,
    n_timesteps,
    timesteps_per_period,
    cash_injection = 0.0,
    fin_obj_count,
    widget_count,
    pay_int_rate = 0.0,
    hold_return_int_rate = 0.0;
    kwargs...
)
```

a simulating environment to test trading or hedging strategies for multiple financial instruments for given interest rates and prices. To be used by providing a new method for the  `strategy()` function which defines the trading strategy. 

Returns the dollar cumulative return from the strategy, the time-series of all holdings  the strategy, and the updated object array. 

## Arguments

  * `objs::Vector{<:FinancialInstrument}`: vector of financial instruments the trading or hedging strategy runs on
  * `pricing_model`: `Model` subtype that defines how to price the `obj`
  * `strategy_type`: `Hedging` subtype that the `strategy()` function dispatches off. Must provide a new subtype for new `strategy()` methods
  * `future_prices`: dictionary of vectors of future prices for underlying `Widget` assets used in financial instruments in `objs`

Note: dictionary keys must be the `widget.name` field string for each base asset

  * `n_timesteps`: number of timesteps to test the strategy on
  * `timesteps_per_period`: for the size of a timestep in the data, the number of

time steps for a given period of time, cannot be negative. For example, if the period of  interest is a year, and daily stock data is used, `timesteps_per_period=252`. Must be positive.

  * `cash_injection`: amount of cash owned when starting the strategy
  * `fin_obj_count`: dictionary of amounts of financial instruments owned when starting the strategy

Note: dictionary keys must be the `FinancialInstrument.label` field string for each financial instrument

  * `widget_count`: dictionary of amounts of base assets used in financial instruments owned when starting the strategy

Note: dictionary keys must be the `Widget.name` field string for each base asset

  * `pay_int_rate`: the continuous interest rate payed on negative cash balances
  * `hold_return_int_rate`: the continous interest rate earned on positive cash balances
  * `kwargs`: pass through for keyword arguments needed by `price!()` or `strategy()` functions

## Example

```
# make the widgets and FinancialInstruments to be used
stock = Stock(; prices=[99, 97, 90, 83, 83, 88, 88, 89, 97, 100], name="stock", timesteps_per_period=252)
stock2 = Stock(; prices=[66, 61, 70, 55, 65, 63, 57, 55, 53, 68], name="stock2", timesteps_per_period=252)
call = EuroCallOption(stock, 110; maturity=.5, label="call", risk_free_rate=.02)
call2 = EuroCallOption(stock2, 70; maturity=1, label="call2", risk_free_rate=.02)
objs = [call, call2]

# make a Dict with future_prices for each widget
future_prices = Dict(
    "stock" => [100, 104, 109, 105, 108, 108, 101, 101, 104, 110],
    "stock2" => [67, 74, 73, 67, 67, 75, 69, 71, 69, 70]
)

# make dictionaries for the starting amounts held of each Widget and FinancialInstrument
fin_obj_count = Dict("call" => 1.0, "call2" => 2)
widget_count = Dict("stock" => 2.0, "stock2" => 3)
cash_injection = 0.0

pay_int_rate = 0.08
hold_return_int_rate = 0.02

cumulative_return, ts_holdings, obj_array = strategy_returns(
    objs, 
    BlackScholes,
    Naked,
    future_prices,
    10,
    252,
    cash_injection,
    fin_obj_count,
    widget_count, 
    pay_int_rate, 
    hold_return_int_rate
)
```
