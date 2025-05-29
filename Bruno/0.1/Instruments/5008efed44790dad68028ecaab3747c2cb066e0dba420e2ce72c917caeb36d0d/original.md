```
Bond(prices, name, time_mat, coupon_rate)
Bond(price; kwargs...)
Bond(;kwargs)
```

Construct a Bond type to use as a base asset for FinancialInstrument.

## Arguments

  * `prices`:Historical prices (input as a 1-D array) or the current price input as a number `<: Real`
  * `name`: String name of the Bond or issuing company. Default "".
  * `time_mat`: Time until the bond expires (matures) in years. Default 1.
  * `coupon_rate`: The coupon rate for the bond. Default .03.

## Examples

```julia
Bond([1,2,3,4,5], "Example", .5, .05)

kwargs = Dict(:prices => [1, 2, 3, 4, 5], :name => "Example", :time_mat => .5, :coupon_rate => .05);
Bond(;kwargs...)

Bond(2; coupon_rate=.05)
```
