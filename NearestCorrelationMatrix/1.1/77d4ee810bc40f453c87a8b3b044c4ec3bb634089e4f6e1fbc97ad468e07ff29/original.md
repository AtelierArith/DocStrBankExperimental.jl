```
autotune(algtype, prob)
```

Initialize an algorithm that is tuned to the NCM problem.

# Examples

```julia-repl
julia> r = Float32[
     1.0     -0.2188  -0.79     0.7773
    -0.2188   1.0      0.2559  -0.5977
    -0.79     0.2559   1.0      0.2266
     0.7773  -0.5977   0.2266   1.0
];

julia> prob = NCMProblem(r);

julia> alg = autotune(Newton, prob);
```
