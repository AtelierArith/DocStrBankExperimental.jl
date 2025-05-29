```
ParallelModel(f::Function, name::Symbol)
```

`ParallelModel`は、`Model`が行うことを少し異なる方法で行います。関数`f`には、全体の`DataFrame`ではなく`DataFrameRow`が渡されます。もしワーカー（`Distributed`を通じて）が存在する場合、行は並列に評価されます。
