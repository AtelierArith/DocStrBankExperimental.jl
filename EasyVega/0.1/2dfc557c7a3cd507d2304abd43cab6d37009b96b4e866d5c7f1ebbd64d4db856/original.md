```
Signal()
```

Create a signal. [Vega docs](https://vega.github.io/vega/docs/signals/)

# Example

```julia
# create a signal linked to a control
sig1 = Signal(value=15, bind=(input=:range, min=0, max=50, step=1))

# create a signal based on an expression
sig2 = Signal(update="[0,0.9*bandwidth('$xscale')]")
```
