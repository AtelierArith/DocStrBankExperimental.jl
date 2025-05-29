```
run_monodromy(F::Union{System, AbstractSystem}, xp₀=nothing; options...) -> SampledSystem
```

与えられた多項式系 `F` に対して、初期解 `xp₀[1]` とパラメータ `xp₀[2]`（指定されている場合）を用いて [`monodromy_solve`](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/monodromy/) を実行します。

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
