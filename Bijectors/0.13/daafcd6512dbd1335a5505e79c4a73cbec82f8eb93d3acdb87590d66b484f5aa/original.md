```
Coupling{F, M}(θ::F, mask::M)
```

Implements a coupling-layer as defined in [1].

# Examples

```jldoctest
julia> using Bijectors: Shift, Coupling, PartitionMask, coupling, couple

julia> m = PartitionMask(3, [1], [2]); # <= going to use x[2] to parameterize transform of x[1]

julia> cl = Coupling(Shift, m); # <= will do `y[1:1] = x[1:1] + x[2:2]`;

julia> x = [1., 2., 3.];

julia> cl(x)
3-element Vector{Float64}:
 3.0
 2.0
 3.0

julia> inverse(cl)(cl(x))
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> coupling(cl) # get the `Bijector` map `θ -> b(⋅, θ)`
Shift

julia> couple(cl, x) # get the `Bijector` resulting from `x`
Shift([2.0])

julia> with_logabsdet_jacobian(cl, x)
([3.0, 2.0, 3.0], 0.0)
```

# References

[1] Kobyzev, I., Prince, S., & Brubaker, M. A., Normalizing flows: introduction and ideas, CoRR, (),  (2019). 
