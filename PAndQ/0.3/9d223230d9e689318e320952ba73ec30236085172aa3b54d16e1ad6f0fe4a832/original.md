```
print_tree(::IO = stdout, p; kwargs...)
```

Print a tree diagram of the given proposition.

Keyword parameters are passed to [`AbstractTrees.print_tree`](https://github.com/JuliaCollections/AbstractTrees.jl/blob/master/src/printing.jl).

```jldoctest
julia> @atomize print_tree(p ∧ q ∨ ¬s)
∨
├─ ∧
│  ├─ 𝒾
│  │  └─ p
│  └─ 𝒾
│     └─ q
└─ ¬
   └─ s

julia> @atomize print_tree(normalize(∧, p ∧ q ∨ ¬s))
∧
├─ ∨
│  ├─ ¬
│  │  └─ s
│  └─ 𝒾
│     └─ q
└─ ∨
   ├─ ¬
   │  └─ s
   └─ 𝒾
      └─ p
```
