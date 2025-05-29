```
SeparateLevel{Lvl, [Val]}()
```

A subfiber of a Separate level is a separate tensor of type `Lvl`, in it's own memory space.

Each sublevel is stored in a vector of type `Val` with `eltype(Val) = Lvl`.

```jldoctest
julia> tensor_tree(Tensor(Dense(Separate(Element(0.0))), [1, 2, 3]))
3-Tensor
└─ Dense [1:3]
   ├─ [1]: Pointer ->
   │  └─ 1.0
   ├─ [2]: Pointer ->
   │  └─ 2.0
   └─ [3]: Pointer ->
      └─ 3.0
```
