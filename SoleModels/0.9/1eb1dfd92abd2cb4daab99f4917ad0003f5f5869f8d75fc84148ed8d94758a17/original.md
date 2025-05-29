```
listimmediaterules(m::AbstractModel{O} where {O})::Rule{<:O}
```

List the immediate rules equivalent to a symbolic model.

# Examples

```julia-repl
julia> using SoleLogics

julia> branch = Branch(SoleLogics.parseformula("p"), Branch(SoleLogics.parseformula("q"), "YES", "NO"), "NO")
 p
├✔ q
│├✔ YES
│└✘ NO
└✘ NO


julia> printmodel.(listimmediaterules(branch); tree_mode = true);
▣ p
└✔ q
 ├✔ YES
 └✘ NO

▣ ¬(p)
└✔ NO


```

See also [`listrules`](@ref), [`AbstractModel`](@ref).
