```
isbounding(ad::AbstractDirections)
isbounding(ad::Type{<:AbstractDirections})
```

Check whether an overapproximation with a set of direction vectors results in a bounded set, given a bounded input set.

### Input

  * `ad` – direction vectors or a subtype of `AbstractDirections`

### Output

Given a bounded set $X$, we can construct an outer polyhedral approximation of $X$ by using the direction vectors `ad` as normal vectors of the facets. If this function returns `true`, then the result is again guaranteed to be a bounded set (i.e., a polytope). Note that the result does not depend on the specific shape of $X$, as long as $X$ is bounded.

### Notes

By default, this function returns `false` in order to be conservative. Custom subtypes of `AbstractDirections` should hence add a method for this function.

The function can be applied to an instance of an `AbstractDirections` subtype or to the subtype itself. By default, the check on the instance falls back to the check on the subtype.
