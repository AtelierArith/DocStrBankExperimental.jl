```
AtomicElementLevel{Vf, [Tv=typeof(Vf)], [Tp=Int], [Val]}()
```

[`ElementLevel`](@ref)のように、レベルへの更新が原子的に行われます。

```jldoctest
julia> tensor_tree(Tensor(Dense(AtomicElement(0.0)), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: 1.0
   ├─ [2]: 2.0
   └─ [3]: 3.0
```
