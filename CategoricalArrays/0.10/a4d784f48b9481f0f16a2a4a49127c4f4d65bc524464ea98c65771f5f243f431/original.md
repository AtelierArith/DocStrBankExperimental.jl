```
levels(x::CategoricalArray; skipmissing=true)
levels(x::CategoricalValue)
```

Return the levels of categorical array or value `x`. This may include levels which do not actually appear in the data (see [`droplevels!`](@ref)). `missing` will be included only if it appears in the data and `skipmissing=false` is passed.

The returned vector is an internal field of `x` which must not be mutated as doing so would corrupt it.
