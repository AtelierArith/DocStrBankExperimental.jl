```
run_monodromy(F::Union{System, AbstractSystem}, xp₀=nothing; options...) -> SampledSystem
```

Runs [`monodromy_solve`](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/monodromy/) on a given polynomial system `F` with starting solutions `xp₀[1]` and parameters `xp₀[2]` (if given).

```julia-repl
julia> @var x a b;

julia> F = System([x^3+a*x+b]; variables=[x], parameters=[a,b]);

julia> F = run_monodromy(F, ([[1]], [1,-2]); max_loops_no_progress = 10)
SampledSystem with 3 samples
 1 unknown: x
 2 parameters: a, b

 number of solutions: 3
 sampled instances: 1
```
