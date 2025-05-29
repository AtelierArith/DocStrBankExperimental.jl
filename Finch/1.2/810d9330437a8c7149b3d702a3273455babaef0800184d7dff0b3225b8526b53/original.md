```
PatternLevel{[Tp=Int]}()
```

A subfiber of a pattern level is the Boolean value true, but it's `fill_value` is false. PatternLevels are used to create tensors that represent which values are stored by other fibers. See [`pattern!`](@ref) for usage examples.

```jldoctest
julia> tensor_tree(Tensor(Dense(Pattern()), 3))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: true
   ├─ [2]: true
   └─ [3]: true
```
