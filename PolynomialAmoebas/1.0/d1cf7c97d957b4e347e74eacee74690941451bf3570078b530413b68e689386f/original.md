```
contour(f; options...)
```

Compute the contour 𝐶(𝑓) of the amoeba $\mathcal{A}(f)$.

## Example

```julia
@polyvar x y

contour(x^2+y^2+1)

# custom domain
contour(x^2+y^2+1, domain=(-5, 5, -5, 5))
```

## Options

  * `domain`: A tuple in the form `(xmin, xmax, ymin, ymax)` which defines a section Ω

for which the contour 𝐶(𝑓) is computed.

  * `membership_options`: The options for the membership test
  * `res=(600,600)`: The resolution with which starting points are sampled
  * `samples_off_axis=2*MP.maxdegree(p)^2`: The number of sample points per off-axis.
