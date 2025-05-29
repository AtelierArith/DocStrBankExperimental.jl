```
joinrules(rules::AbstractVector{<:Rule})::Vector{<:Rule}
```

Return a set of rules, with exactly one rule per different outcome from the input set of rules. For each outcome, the output rule is computed as the logical disjunction of the antecedents of the input rules for that outcome.

# Examples

```julia-repl
julia> using SoleLogics

julia> branch = Branch(SoleLogics.parseformula("p"), Branch(SoleLogics.parseformula("q"), "YES", "NO"), "NO")
 p
├✔ q
│├✔ YES
│└✘ NO
└✘ NO


julia> printmodel.(listrules(branch); tree_mode = true);
▣ p ∧ q
└✔ YES

▣ p ∧ ¬q
└✔ NO

▣ ¬p
└✔ NO

julia> printmodel.(joinrules(listrules(branch)); tree_mode = true);
▣ (p ∧ q)
└✔ YES

▣ (p ∧ ¬q) ∨ ¬p
└✔ NO

```

See also [`listrules`](@ref), [`SoleLogics.DISJUNCTION`](@ref), [`LeafModel`](@ref), [`AbstractModel`](@ref).
