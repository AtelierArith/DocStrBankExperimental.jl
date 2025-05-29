```
lift_comparison!(cmp, compact::IncrementalCompact, idx::Int, stmt::Expr, 𝕃ₒ::AbstractLattice)
```

`cmp(φ(x, y)::Union{X,Y}, constant)` を `φ(cmp(x, constant), cmp(y, constant))` に置き換えます。ここで、`cmp(x, constant)` と `cmp(y, constant)` は定数の `Bool` に置き換えることができます。これにより、コード生成が `Union` 型の `cmp` に対して高コストなコードを生成するのを避けるのに役立ちます。特に、これはイテレーションプロトコルのパフォーマンスを改善することを目的としています：

```julia
while x !== nothing
    x = iterate(...)::Union{Nothing,Tuple{Any,Any}}
end
```
