```
MullerBrown(; A, a, b, c, x0, y0, force_units, energy_units)
```

The Müller-Brown potential energy surface implemented as an AtomsCalculators.jl calculator.

The potential energy is defined as

$$
V(x,y) = \sum_{n=1}^{4} A_k \exp[a_k(x-x_k^0)^2 + b_k(x-x_k^0)(y-y_k^0) + c_k(y-y_k^0)^2]
$$

where `A`, `a`, `b`, `c`, `x0`, `y0` are 4-element `SVector`s with standard defaults.

This potential is only compatible with 2D systems. It is often used for testing algorithms that find transition states or explore minimum energy pathways. There are 3 minima and 2 saddle points with the default parameters.
