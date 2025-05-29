```
coamoeba(f; alg=Greedy(), options...)
```

Compute the coamoeba of `f` with the given algorithm `alg` which can be

  * `Greedy()`
  * `Coarse()`
  * `Simple()`

but you probably only want to use `Greedy()` or `Coarse`.

The coamoeba is embedded in $[0, 2π)^n$ where $n$ is either 2 or 3 depending on the polynomial. The algorithm approximate the coamoeba on a grid representing this embedding.

## Example

```julia
@polyvar x y

# This uses the `Greedy()` algorithm
coamoeba(x^2 + y^2 + 1)
```

## Optional arguments

  * `resolution=600`: The resolution of the grid if not passed explicitly.
  * `membership_options=[MembershipTestOptions()](@ref)`: The options for the membership test.
  * `test_domain`: Tuple `(xmin, xmax, ymin, ymax)` resp. `(xmin, xmax, ymin, ymax, zmin, zmax)`

from which start values for the membership test are drawn if necessary.
