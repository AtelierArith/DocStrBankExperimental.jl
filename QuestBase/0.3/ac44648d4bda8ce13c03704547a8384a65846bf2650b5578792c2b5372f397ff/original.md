```julia
add_harmonic!(
    diff_eom::QuestBase.DifferentialEquation,
    var::Symbolics.Num,
    ω
)

```

Add the harmonic `ω` to the harmonic ansatz used to expand the variable `var` in `diff_eom`.

## Example

# define the simple harmonic oscillator and specify that x(t) oscillates with frequency ω

```julia-repl
julia> @variables t, x(t), y(t), ω0, ω, F, k;
julia> diff_eq = DifferentialEquation(d(x,t,2) + ω0^2 * x ~ F * cos(ω*t), x);
julia> add_harmonic!(diff_eq, x, ω) # expand x using ω

System of 1 differential equations
Variables:       x(t)
Harmonic ansatz: x(t) => ω;

(ω0^2)*x(t) + Differential(t)(Differential(t)(x(t))) ~ F*cos(t*ω)
```
