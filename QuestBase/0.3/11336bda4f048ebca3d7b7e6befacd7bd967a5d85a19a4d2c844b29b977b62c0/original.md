```julia
mutable struct DifferentialEquation
```

Holds differential equation(s) of motion and a set of harmonics to expand each variable. This is the primary input for `HarmonicBalance.jl`. After inputting the equations, the harmonics ansatz needs to be specified using `add_harmonic!`.

# Fields

  * `equations::OrderedCollections.OrderedDict{Symbolics.Num, Symbolics.Equation}`: Assigns to each variable an equation of motion.
  * `harmonics::OrderedCollections.OrderedDict{Symbolics.Num, OrderedCollections.OrderedSet{Symbolics.Num}}`: Assigns to each variable a set of harmonics.

## Example

```julia-repl
julia> @variables t, x(t), y(t), ω0, ω, F, k;

# equivalent ways to enter the simple harmonic oscillator
julia> DifferentialEquation(d(x,t,2) + ω0^2 * x - F * cos(ω*t), x);
julia> DifferentialEquation(d(x,t,2) + ω0^2 * x ~ F * cos(ω*t), x);

# two coupled oscillators, one of them driven
julia> DifferentialEquation(
    [d(x,t,2) + ω0^2 * x - k*y, d(y,t,2) + ω0^2 * y - k*x] .~ [F * cos(ω*t), 0], [x,y]
);
```
