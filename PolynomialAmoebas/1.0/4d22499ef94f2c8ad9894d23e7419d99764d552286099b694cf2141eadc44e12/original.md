```
amoeba(f; alg=Polygonal(), options...)
```

Compute the amoeba of `f` with the given algorithm `alg` which can be

  * `Polygonal()`
  * `Greedy()`
  * `ArchTrop()`
  * `Simple()`

but you probably only want to use `Polygonal()` or `Greedy()`.

Depending on the given algorithm the function takes different keyword arguments.

## Examples

```julia
@polyvar x y

# This uses the `Polygonal()` algorithm
amoeba(x^2 + y^2 + 1)

# We only want a crude approximation
amoeba(x^2 + y^2 + 1, accuracy=0.1)

# Use the `Greedy()` algorithm.
amoeba(x^2 + y^2 + 1, alg=Greedy())

# Use the `Greedy()` algorithm with a custom grid.
grid = Grid2D(xlims=(-5, 5), ylims=(-4, 4), res=(500, 400))
amoeba(x^2 + y^2 + 1, alg=Greedy(), grid=grid)

# Use the `Greedy()` algorithm with the default domain but a higher resolution
amoeba(x^2 + y^2 + 1, alg=Greedy(), resolution=800)
```

## `Polygonal()`

This algorithm computes an approximation of the amoeba $\mathcal{A}(f)$ in the provided `domain` Ω by computing a set of polygons 𝒫 with |𝒫| ⊂ Ω such that the union of these polygons approximates $\mathcal{A}(f)$ ∩ Ω from the outside.

The possible (optional) arguments are

  * `domain`: A tuple in the form `(xmin, xmax, ymin, ymax)` which defines a section Ω

for which the amoeba $\mathcal{A}(f)$ is computed. This domain has to be such that the intersection Ω ∩ $\mathcal{A}(f)$ still captures the correct topology of $\mathcal{A}(f)$.

  * `accuracy=0.01`: The maximal allowed error |𝒫 - $\mathcal{A}(f)$ ∩ Ω|. Note that we only compute an upper limit of the error.

The algorithms stops if the given accuracy is reached.

  * `spine`: This algorithm needs the spine of $\mathcal{A}(f)$.
  * `minimal_component_size=0.01`: The minimal size of the components of the complement. This is only used if no spine

is passed explicitly.

  * `iterations=2000`: The maximal number of iterations.
  * `vertices_accuracy=accuracy*1e-3`: During the algorithm we approximate points on the boundary of $\mathcal{A}(f)$. This

is the accuracy with which we compute them. Note hat this influences the minimal error of the approximation and it should always be some magnitudes smaller than `accuracy`.

  * `membership_options=[MembershipTestOptions()](@ref)`: As a subroutine a membership test is used.

## `Greedy()`, `Simple()`, `ArchTrop()`

These algorithms are all approximations of the amoeba $\mathcal{A}(f)$ based on a grid. This basically applies the membership test for different grid points. `Greedy()` is the fastest and `Simple()` the slowest. The grid can be passed explicitly, otherwise it will be computed based on a heuristic.

  * `resolution=600`: The resolution of the grid if not passed explicitly.
  * `grid`: If passed explicitly this grid is used, otherwise it will be computed based on a heuristic.
  * `membership_options=[MembershipTestOptions()](@ref)`: The options for the membership test.
