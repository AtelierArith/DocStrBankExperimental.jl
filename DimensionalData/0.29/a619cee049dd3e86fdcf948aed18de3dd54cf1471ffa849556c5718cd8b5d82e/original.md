```
@d broadcast_expression options
```

Dimensional broadcast macro extending Base Julia broadcasting to work with missing and permuted dimensions.

Will permute and reshape singleton dimensions so that all [`AbstractDimArray`](@ref) in a broadcast will broadcast over matching dimensions.

It is possible to pass options as the second argument of  the macro to control the behaviour, as a single assignment or as a NamedTuple. Options names must be written explicitly, not passed in namedtuple variable.

# Options

  * `dims`: Pass a Tuple of `Dimension`s, `Dimension` types or `Symbol`s   to fix the dimension order of the output array. Otherwise dimensions   will be in order of appearance. If dims with lookups are passed, these will    be applied to the returned array with  `set`.
  * `strict`: `true` or `false`. Check that all lookup values match explicitly.

All other keywords are passed to `DimensionalData.rebuild`. This means `name`, `metadata`, etc for the returned array can be set here,  or for example `missingval` in Rasters.jl.

# Example

```julia
using DimensionalData
da1 = ones(X(3))
da2 = fill(2, Y(4), X(3))

@d da1 .* da2
@d da1 .* da2 .+ 5 dims=(Y, X)
@d da1 .* da2 .+ 5 (dims=(Y, X), strict=false, name=:testname)
```

## Use with `@.`

`@d` does not imply `@.`. You need to specify each broadcast.  But `@.` can be used with `@d` as the *inner* macro.

```julia
using DimensionalData
da1 = ones(X(3))
da2 = fill(2, Y(4), X(3))

@d @. da1 * da2
# Use parentheses around `@.` if you need to pass options
@d (@. da1 * da2 .+ 5) dims=(Y, X)
```
