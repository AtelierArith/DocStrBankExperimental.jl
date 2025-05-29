```
SourceTermDamping(; damping_coefficient)
```

A source term to be used when a damping step is required before running a full simulation. The term $-c \cdot v_a$ is added to the acceleration $\frac{\mathrm{d}v_a}{\mathrm{d}t}$ of particle $a$, where $c$ is the damping coefficient and $v_a$ is the velocity of particle $a$.

# Keywords

  * `damping_coefficient`:    The coefficient $d$ above. A higher coefficient means more                           damping. A coefficient of `1e-4` is a good starting point for                           damping a fluid at rest.

# Examples

```jldoctest; output = false
source_terms = SourceTermDamping(; damping_coefficient=1e-4)

# output
SourceTermDamping{Float64}(0.0001)
```
