```julia
renormed(model, f)

```

モデル `m` を総フラックス `f*flux(m)` に正規化します。これは、`Base.:*` を直接呼び出すことでも行うことができます。すなわち、

```julia-repl
julia> renormed(m, f) == f*M
true
```
