```
imaginary_projection(f; alg=Greedy(), grid=..., options...)
```

Compute the imaginary_projection of `f` with the given algorithm `alg` and a 2D or 3D grid. `alg` can be

  * `Greedy()`
  * `Simple()`

but you probably only want to use `Greedy()`.

## Examples

```julia
@polyvar x y

g = x^4 + im * x^3 - x^2 * y^2 + 3x^3 - 2im*x*y^2 + (4-2im)*x + 0.5*y^2 + 1.5
grid = Grid2D(xlims=(-4, 4), ylims=(-5, 5), res=(1200, 1200))
# This uses the `Greedy()` algorithm
imaginary_projection(g, grid=grid)
```

These algorithms are all approximations of the imaginary projection 𝐼(𝑓) based on a grid. This basically applies the membership test for different grid points. The grid can be passed explicitly, otherwise it will be computed based on a heuristic.

  * `membership_options=[MembershipTestOptions()](@ref)`: The options for the membership test.
  * `npasses=1`: The `Greedy()` algorithm can make multiple passes to improve the quality.
  * `test_domain`: A tuple `(xmin, xmax, ymin, ymax, [zmin, zmax])` from which start values for the membership test are drawn.
