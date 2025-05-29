```
Commodity(prices, name, timesteps_per_period, volatility)
commodity(price; kwargs...)
Commodity(;kwargs)
```

Construct a Commodity type to use as a base asset for FinancialInstrument.

## Arguments

  * `prices`:Historical prices (input as a 1-D array) or the current price input as a number `<: Real`
  * `name`: String name of the commodity or commodity ticker symbol. Default "".
  * `timesteps_per_period`: For the size of a timestep in the data, the number of

time steps for a given period of time, cannot be negative. For example, if the period of  interest is a year, and daily commodity price data is used, `timesteps_per_period=252`.  Defualt is the length of the `prices` array or 0 for a single price (static) Commodity.  Note: If `timesteps_per_period=0`, the Commodity represents a 'static' element and cannot  be used in the `strategy_returns()` method.

  * `volatility`: Return volatility, measured in the standard deviation of continuous returns.

Defaults to using `get_volatility()` on the input `prices` array. Note: if a single number  is given for `prices` volatility must be given.

## Examples

```julia
Commodity([1,2,3,4,5], "Example", 252, .05)

kwargs = Dict(
    :prices => [1, 2, 3, 4, 5], 
    :name => "Example", 
    :timesteps_per_period => 252, 
    :volatility => .05
);

Commodity(;kwargs...)

Commodity(40; volatility=.05)
```
