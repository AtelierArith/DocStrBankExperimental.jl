```
spine(f::MP.AbstractPolynomial; options...)
```

Compute the spine of the amoeba $\mathcal{A}(f)$. This algorithm computes first an approximation of $\mathcal{A}(f)$ and from this the spine. Returns a Spine2D.

## Example

```julia
@polyvar x y
# use all the defaults
spine(x^2 + y^2 + 1)

# Maybe we think that the compleement of the amoeba has some very small components
# and we want to use an explicit domain
spine(x^2 + y^2 + 1, domain=(-5, 5, -5, 5), minimal_component_size=0.001)
```

Optional arguments:

  * `minimal_component_size=0.01`: A guarantee that in each component of the complement of $\mathcal{A}(f)$ fits a ball with this diameter.

If this does not hold the algorithm can return a wrong result.

  * `domain`: A tuple in the form `(xmin, xmax, ymin, ymax)` which defines a section Ω

for which the amoeba $\mathcal{A}(f)$ is computed. This domain has to be such that the intersection Ω ∩ $\mathcal{A}(f)$ still captures the correct topology of $\mathcal{A}(f)$.

  * `grid`: Based on `minimal_component_size` and `domain` a grid can be computed automatically.

This can also be overwritten with this option.

  * `membership_options=[MembershipTestOptions](@ref)()`: Options for the membership test.
  * `nsamples=1024`: For the computation we numerically evaluate intergrals. This is the number

of sample points used in the computation.

```
spine(f::MP.AbstractPolynomial, A::Bitmap2D; nsamples=1024)
```

Compute the spine based on the given amoeba approximation `A`.
