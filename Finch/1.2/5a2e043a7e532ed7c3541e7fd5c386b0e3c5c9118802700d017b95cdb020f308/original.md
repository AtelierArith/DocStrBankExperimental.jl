```
AtomicElementLevel{Vf, [Tv=typeof(Vf)], [Tp=Int], [Val]}()
```

Like an [`ElementLevel`](@ref), but updates to the level are performed atomically.

```jldoctest
julia> tensor_tree(Tensor(Dense(AtomicElement(0.0)), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: 1.0
   ├─ [2]: 2.0
   └─ [3]: 3.0
```
