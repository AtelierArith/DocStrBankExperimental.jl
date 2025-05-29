```
strategy_returns(
    obj::FinancialInstrument,
    pricing_model,
    strategy_type,
    future_prices,
    n_timesteps,
    timesteps_per_period,
    cash_injection = 0.0,
    fin_obj_count = 0.0,
    widget_count = 0.0,
    pay_int_rate = 0.0,
    hold_return_int_rate = 0.0;
    kwargs...
)
```

a simulating environment to test trading or hedging strategies for given interest rates and  and prices. To be used by providing a new method for the `strategy()` function which defines  the trading strategy. 

Returns the dollar cumulative return from the strategy, the time-series of all holdings  the strategy, and the updated object array. 

## Arguments

  * `obj`: financial instrument the trading or hedging strategy runs on
  * `pricing_model`: `Model` subtype that defines how to price the `obj`
  * `strategy_type`: `Hedging` subtype that the `strategy()` function dispatches off. Must provide a new subtype for new `strategy()` methods
  * `future_prices`: vector of future prices for the underlying `Widget` asset of obj to run strategy on
  * `n_timesteps`: number of timesteps to test the strategy on
  * `timesteps_per_period`: for the size of a timestep in the data, the number of

time steps for a given period of time, cannot be negative. For example, if the period of  interest is a year, and daily stock data is used, `timesteps_per_period=252`. Must be positive.

  * `cash_injection`: amount of cash owned when starting the strategy
  * `fin_obj_count`: amount of financial instruments owned when starting the strategy
  * `widget_count`: amount of underlying `Widget` owned when starting the strategy
  * `pay_int_rate`: the continuous interest rate payed on negative cash balances
  * `hold_return_int_rate`: the continous interest rate earned on positive cash balances
  * `kwargs`: pass through for keyword arguments needed by `price!()` or `strategy()` functions

## Example

```
# make the Widget and FinancialInstrument to be used
stock = Stock(; prices=[99, 97, 90, 83, 83, 88, 88, 89, 97, 100], name="stock", timesteps_per_period=252)
call = EuroCallOption(stock, 110; maturity=.5, label="call", risk_free_rate=.02)

# make future_prices array
future_prices = [100, 104, 109, 105, 108, 108, 101, 101, 104, 110]

fin_obj_count = 2
widget_count = 3
pay_int_rate = .05
hold_return_int_rate = .02

cumulative_return, ts_holdings, obj = strategy_returns(
    call, 
    BlackScholes,
    Naked,
    future_prices,
    10,
    252, 
    10.0, 
    fin_obj_count, 
    widget_count,
    pay_int_rate, 
    hold_return_int_rate;
    transaction_cost = 0.0
)
```
