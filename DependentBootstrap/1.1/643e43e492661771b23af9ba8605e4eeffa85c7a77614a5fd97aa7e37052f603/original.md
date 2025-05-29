Module for dependent bootstrap procedures, by Colin T Bowers

Implemented bootstrap methods: 

```
- IID
- Stationary
- Moving Block
- Circular Block
- NoOverlapBlock
```

Implemented block length selection procedures: 

```
- Patton, Politis, and White (2009) Correction to Automatic Block Length Selection For The Dependent Bootstrap
```

Accepted input dataset types: 

```
- Vector{<:Number}
- Matrix{<:Number} (where rows are observations and columns are variables)
- Vector{Vector{<:Number}} (where elements of inner vectors are observations and outer vectors are variables)
- DataFrame
- TimeSeries.TimeArray{T,N} (only for N = 1 and N = 2)
```

Additional input dataset types are easily added. Please open an issue at https://github.com/colintbowers/DependentBootstrap.jl

The module has only a single exported type: 

```
- BootInput  <-- Core input type accepted by all exported functions. Typically constructed via keyword method. See ?BootInput for more detail.
```

All exported functions exhibit the following keyword signatures: 

```
- exported_func(data, bootinput::BootInput)
- exported_func(data ; kwargs...)
```

Most users will be content to use the keyword argument method. In practice, this method wraps a keyword argument BootInput constructor, which is then input to the exported function BootInput method. For more detail on accepted keywords, see ?BootInput. All exported functions then use the input dataset and bootstrap methodology described in BootInput in order to return the appropriate statistics. A list of exported functions follows: 

```
- optblocklength <-- Estimate the optimal block length for the input dataset
- dbootinds      <-- Get a vector of bootstrap resampling indices
- dbootdata      <-- Get a vector of resampled datasets
- dbootlevel1    <-- Get a vector of level 1 resampled bootstrap statistics
- dboot          <-- Get the level 2 bootstrap statistic
- dbootlevel2    <-- Identical to dboot. Included for completeness
- dbootvar       <-- Wrapper on dboot that sets the level 2 statistic as the variance
- dbootconf      <-- Wrapper on dboot that sets the level 2 statistic as a confidence interval
```

I use the phrases level 1 and level 2 statistics in this package in the same manner discussed in Chapter 1 of Lahiri's textbook Resampling Methods for Dependent Data.

This package has an MIT license. Please see associated LICENSE.md file for more detail.
