```
TurkieCallback(args...; kwargs....)
```

## Arguments

  * Option 1 :    `model::DynamicPPL.Model, plots::Series/AbstractVector=[:histkde, Mean(Float32), Variance(Float32), AutoCov(20, Float32)]`

For each of the variables of the given model each `plot` from `plots` will be plotted Multidimensional variable will be automatically have indices added to them

  * Option 2 :   `vars::NamedTuple/Dict`

Will plot each pair of symbol and series of plots. Note that for multidimensional variable you should pass a Symbol as `Symbol("m[1]")` for example. See the docs for some examples.

## Keyword arguments

  * `window=1000` : Use a window for plotting the trace
  * `refresh=false` : Restart the plots from scratch everytime `sample` is called again (still WIP)
