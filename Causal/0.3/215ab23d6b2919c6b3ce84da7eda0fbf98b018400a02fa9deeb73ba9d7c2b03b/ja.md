```julia
breakloop!(model, loop)
breakloop!(model, loop, breakpoint)

```

モデルの代数的な `loop` を中断します。`model` の `loop` は、ループの `breakpoint` に `Memory` を挿入することで中断されます。
