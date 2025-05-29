```
strategy(
    fin_obj::FinancialInstrument,
    pricing_model, 
    strategy_model, 
    holdings, 
    step;
    kwargs...
)
```

function to be used with `strategy_returns()` function. `strategy()` function defines  buying and selling behavior for a given trading or hedging strategy. To use with  `strategy_returns()` function, define a new `Hedging` subtype to allow for dispatch and write  a new method for `strategy()` dispatcing off this new type in the `strategy_mode` argument.  See package documentation for more information.

## Arguments

  * `fin_obj`: the FinancialInstrument the strategy is defined for
  * `pricing_model`: the pricing model used by the `price!()` function to price the FinancialInstrument
  * `holdings`: the dictionary of current holdings of FinancialInstruments and base assets supplied by the `strategy_returns()` function
  * `step`: the step number out of `n_timesteps` the `strategy_returns` is currently executing
