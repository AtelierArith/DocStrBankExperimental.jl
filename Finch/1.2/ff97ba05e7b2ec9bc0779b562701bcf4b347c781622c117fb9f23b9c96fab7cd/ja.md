```
MutexLevel{Val, Lvl}()
```

ミューテックスレベルは、その下のレベルをアトミックで保護します。

ミューテックスレベルの下の各位置は、ロックによって保護されています。

```jldoctest
julia> tensor_tree(Tensor(Dense(Mutex(Element(0.0))), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: Mutex ->
   │  └─ 1.0
   ├─ [2]: Mutex ->
   │  └─ 2.0
   └─ [3]: Mutex ->
      └─ 3.0
```
