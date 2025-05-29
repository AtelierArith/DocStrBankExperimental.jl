```
lift_comparison!(cmp, compact::IncrementalCompact, idx::Int, stmt::Expr, 𝕃ₒ::AbstractLattice)
```

Replaces `cmp(φ(x, y)::Union{X,Y}, constant)` by `φ(cmp(x, constant), cmp(y, constant))`, where `cmp(x, constant)` and `cmp(y, constant)` can be replaced with constant `Bool`eans. It helps codegen avoid generating expensive code for `cmp` with `Union` types. In particular, this is supposed to improve the performance of the iteration protocol:

```julia
while x !== nothing
    x = iterate(...)::Union{Nothing,Tuple{Any,Any}}
end
```
