```
relerrorthreshold(coef, [redundant, tree, elbows; makeplot])
```

Takes in a set of expansion coefficients, 'plot' the threshold vs relative error curve and select the best threshold value based on the elbow method. If one wants to see the resulting plot from this computation, simply set `makeplot=true`.

# Arguments

  * `coef::AbstractArray{T} where T<:Number`: Decomposed signal.
  * `redundant::Bool`: (Default: `false`) Whether the transform type of `xw` is a redundant transform. Autocorrelation and stationary wavelet transforms are examples of redundant transforms.
  * `tree::Union{BitVector, Nothing}`: (Default: `nothing`) The basis tree for decomposing `xw`. Must be provided if `xw` is decomposed using `swpd` or `acwpd`.
  * `elbows::Integer`: (Default: 2) Number of elbows used to determine the best threshold value.

# Keyword Arguments

  * `makeplot::Bool`: (Default: `false`) Whether to return the plot that was used to determine the best threshold value.

# Returns

  * `::AbstractFloat`: Best threshold value.
  * `::GR.Plot`: Plot that was used to determine the best threshold value. Only returned if `makeplot = true`.

# Examples

```julia
x = randn(128)
wt = wavelet(WT.haar)

# noise estimate for dwt transformation
y = dwt(x, wt)
noise = relerrorthreshold(y, false)

# noise estimate for wpt transformation
tree = maketree(x, :full)
y = wpt(x, wt, tree)
noise = relerrorthreshold(y, false, tree)

# noise estimate for sdwt transformation
y = sdwt(x, wt)
noise = relerrorthreshold(y, true)

# noise estimate for swpd transformation
y = swpd(x, wt)
noise = relerrorthreshold(y, true, tree)
```

**See also:** [`noisest`](@ref), [`RelErrorShrink`](@ref)
