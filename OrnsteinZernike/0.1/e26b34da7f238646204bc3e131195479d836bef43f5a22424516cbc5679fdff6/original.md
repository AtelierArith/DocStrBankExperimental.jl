```
CharpentierJackse <: Closure
```

Implements the Charpentier-Jackse closure $b(r) = \frac{1}{2\alpha}\left(\sqrt{1+4\alpha\gamma^*(r) } - 2\alpha\gamma^*(r) - 1\right) $. Here  $\gamma^* = \gamma - u_{LR}$ , in which $ u_{LR}$ is the long range tail of the potential, and $\alpha$ is a free parameter that  can be determined with thermodynamic consistency.

Example:

```julia
closure = CharpentierJackse(0.5)
```

References:

Charpentier, I., and N. Jakse. "Exact numerical derivatives of the pair-correlation function of simple liquids using the tangent linear method." The Journal of Chemical Physics 114.5 (2001): 2284-2292.
