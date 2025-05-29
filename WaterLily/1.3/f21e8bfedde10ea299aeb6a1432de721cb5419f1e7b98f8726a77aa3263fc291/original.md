```
measure!(flow::Flow, body::AbstractBody; t=0, ϵ=1)
```

Queries the body geometry to fill the arrays:

  * `flow.μ₀`, Zeroth kernel moment
  * `flow.μ₁`, First kernel moment scaled by the body normal
  * `flow.V`,  Body velocity

at time `t` using an immersion kernel of size `ϵ`.

See Maertens & Weymouth, doi:[10.1016/j.cma.2014.09.007](https://doi.org/10.1016/j.cma.2014.09.007).
