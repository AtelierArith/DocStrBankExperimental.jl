```julia
struct TimeDependentCoupling
```

Defines a single time dependent system bath coupling operator. It is defined as $S(s)=∑f(s)×M$.  Keyword argument `unit` set the unit one – `:h` or `:ħ`.

# Fields

  * `funcs`: 1-D array of time dependent functions
  * `mats`: 1-D array of constant matrics

# Examples

```julia-repl
julia> TimeDependentCoupling([(s)->s], [σz], unit=:ħ)
```
