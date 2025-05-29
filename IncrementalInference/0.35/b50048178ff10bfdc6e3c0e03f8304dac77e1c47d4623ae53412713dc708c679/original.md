```julia
calcPerturbationFromVariable(fgc, from_var_ipc; tol)

```

Return a tuple of infoPerCoord vectors that result from input variables as vector of `::Pair`, i.e. `fromVar::Int => infoPerCoord`. For example, a binary `LinearRelative` factor has a one-to-one influence from the input to the one other variable.

Notes

  * Assumes the gradients in `fgc` are up to date – if not, first run `fgc(measurement..., pts...)`.
  * `tol` does not recalculate the gradients to a new tolerance, instead uses the cached value in `fgc` to predict accuracy.

Example

```julia
# setup
fct = LinearRelative(MvNormal([10;0],[1 0; 0 1]))
measurement = ([10.0;0.0],)
varTypes = (ContinuousEuclid{2}, ContinuousEuclid{2})
pts = ([0;0.0], [9.5;0])

# create the gradients functor object
fgc = FactorGradientsCached!(fct, varTypes, measurement, pts);
# must first update the cached gradients
fgc(measurement..., pts...)

# check the perturbation influence through gradients on factor
ret = calcPerturbationFromVariable(fgc, [1=>[1;1]])

@assert isapprox(ret[2], [1;1])
```

DevNotes

  * FIXME Support n-ary source factors by extending `fromVar` to more than just one.

Related

[`FactorGradientsCached!`](@ref), [`checkGradientsToleranceMask`](@ref)
