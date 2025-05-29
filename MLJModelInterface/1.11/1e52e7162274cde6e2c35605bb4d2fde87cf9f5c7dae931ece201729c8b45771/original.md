```
params(m::MLJType)
```

Recursively convert any transparent object `m` into a named tuple, keyed on the fields of `m`. An object is *transparent* if `MLJModelInterface.istransparent(m) == true`. The named tuple is possibly nested because `params` is recursively applied to the field values, which themselves might be transparent.

Most objects of type `MLJType` are transparent.

```julia-repl
julia> params(EnsembleModel(model=ConstantClassifier()))
(model = (target_type = Bool,),
 weights = Float64[],
 bagging_fraction = 0.8,
 rng_seed = 0,
 n = 100,
 parallel = true,)
```
