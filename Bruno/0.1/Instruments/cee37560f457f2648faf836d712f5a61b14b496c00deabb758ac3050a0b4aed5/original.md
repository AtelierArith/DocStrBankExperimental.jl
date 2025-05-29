```
EuroCallOption(;kwargs...)
EuroCallOption(widget, strike_price, maturity, risk_free_rate, values_library)
```

Construct a EuroCallOption with underlying asset of type `Widget`

## Arguments

  * `widget`: underlying asset
  * `strike_price`: Contracted price to buy underlying asset at maturity
  * `maturity`: time to maturity of the option with respect to implicit time period. Default 1.
  * `risk_free_rate`: market risk free interest rate. Default is .02.
  * `values_library`: A dictionary of values returned from pricing functions. Default initializes

to an empty dictionary. use `price!()` function to load theoretical option prices.

## Examples

```julia
stock = Stock([1,2,4,3,5,3]);

EuroCallOption(stock, 10)

kwargs = Dict(:widget=>stock, :strike_price=>10, :maturity=>1, :risk_free_rate=>.02);
EuroCallOption(;kwargs...)
```
