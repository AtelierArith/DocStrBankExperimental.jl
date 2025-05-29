```
minimax(r::Barycentric, f::Function, nsteps::Integer=20)
minimax(r::Approximation, nsteps::Integer=20)
```

Compute an approximately minimax rational approximation to a function `f` on the nodes of a given rational function in barycentric form. The returned approximation has the same type as the first input argument.

The `nsteps` argument controls the number of Lawson iterations. The default value is 20.

# Examples

```julia-repl
julia> f(x) = tanh( 40*(x - 0.15) );

julia> r = approximate(f, unit_interval, max_degree=8);  # least-squares approximation

julia> check(r);
[ Info: Max error is 1.06e-02

julia> r̂ = minimax(r);

julia> check(r̂);
[ Info: Max error is 1.40e-03
```
