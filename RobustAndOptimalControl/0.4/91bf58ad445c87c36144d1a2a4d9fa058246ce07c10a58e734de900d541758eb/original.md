```
makeweight(low, f_mid, high)
makeweight(low, (f_mid, gain_mid), high)
```

Create a weighting function that goes from gain `low` at zero frequency, through gain `gain_mid` to gain `high` at ∞

# Arguments:

  * `low`: A number specifying the DC gain
  * `mid`: A number specifying the frequency at which the gain is 1, or a tuple `(freq, gain)`. If `gain_mid` is not specified, the geometric mean of `high` and `low` is used.
  * `high`: A number specifying the gain at ∞

```@example
using ControlSystemsBase, Plots
W = makeweight(10, (5,2), 1/10)
bodeplot(W)
hline!([10, 2, 1/10], l=(:black, :dash), primary=false)
vline!([5], l=(:black, :dash), primary=false)
```
