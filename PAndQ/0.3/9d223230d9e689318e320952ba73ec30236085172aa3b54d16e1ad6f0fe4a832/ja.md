```
print_tree(::IO = stdout, p; kwargs...)
```

与えられた命題のツリーダイアグラムを印刷します。

キーワードパラメータは [`AbstractTrees.print_tree`](https://github.com/JuliaCollections/AbstractTrees.jl/blob/master/src/printing.jl) に渡されます。

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
