```
transfer(f::T, sdof::Oscillator) where {T<:Real}
```

Compute the modulus of the transfer function for a SDOF system.

The transfer function is defined as:

$$
|H(f,f_n,\zeta_n)| = \frac{1}{\sqrt{ \left(1 - \beta^2 \right)^2 + \left(2\zeta_n\beta\right)^2 }}
$$

where $\beta$ is the tuning ratio defined by $f/f_n$.

# Examples

```julia-repl
    f = 2.0
    sdof = Oscillator(1.0, 0.05)
    Hf = transfer(f, sdof)
```

See also: [`squared_transfer`](@ref)
