```
autotune(algtype, prob)
```

NCM問題に調整されたアルゴリズムを初期化します。

# 例

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
