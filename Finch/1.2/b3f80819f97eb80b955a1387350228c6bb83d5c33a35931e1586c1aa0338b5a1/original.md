```
ElementLevel{Vf, [Tv=typeof(Vf)], [Tp=Int], [Val]}()
```

A subfiber of an element level is a scalar of type `Tv`, initialized to `Vf`. `Vf` may optionally be given as the first argument.

The data is stored in a vector of type `Val` with `eltype(Val) = Tv`. The type `Tp` is the index type used to access Val.

```jldoctest
julia> tensor_tree(Tensor(Dense(Element(0.0)), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: 1.0
   ├─ [2]: 2.0
   └─ [3]: 3.0
```
