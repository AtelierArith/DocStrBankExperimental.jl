```
AmericanCallOption(widget, strike_price; kwargs...)
AmericanCallOption(;kwargs...)
```

Construct a AmericanCallOption with underlying asset of type `Widget`

## Arguments

  * `widget`: The underlying asset
  * `strike_price`: Contracted price to buy underlying asset at maturity.
  * `maturity`: time to maturity of the option with respect to implicit time period. Default 1.
  * `risk_free_rate`: market risk free interest rate. Default is .02.
  * `values_library`: The values returned from pricing models. Default initializes

to an empty dictionary. use `price!()` function to load theoretical option prices.

## Examples

```julia
stock = Stock([1,2,4,3,5,3]);

AmericanCallOption(stock, 10)

kwargs= Dict(:widget=>stock, :strike_price=>10, :maturity=>1, :risk_free_rate=>.02);
AmericanCallOption(;kwargs...)
```
