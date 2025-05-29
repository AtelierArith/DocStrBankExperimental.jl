```
dG_o_dT2s_x_T2s_lorentzian(κ)
```

Evaluate the derivative of Green's function, corresponding to a Lorentzian lineshape, wrt. `T2s` at `κ = (t-τ)/T2s` and multiply it by `T2s`.

The multiplication is added so that the function merely depends on `κ = (t-τ)/T2s`. The actual derivative is given by `dG_o_dT2s_x_T2s_lorentzian((t-τ)/T2s)/T2s`.

# Examples

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> dGdT2s = dG_o_dT2s_x_T2s_lorentzian((t-τ)/T2s)/T2s
45.39992976248485
```
