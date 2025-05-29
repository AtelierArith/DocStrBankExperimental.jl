```
listrules(
    m::AbstractModel;
    use_shortforms::Bool = true,
    use_leftmostlinearform::Union{Nothing,Bool} = nothing,
    normalize::Bool = false,
    force_syntaxtree::Bool = false,
)::Vector{<:Rule}
```

Return a list of rules capturing the knowledge enclosed in symbolic model. The behavior of any symbolic model can be synthesised and represented as a set of mutually exclusive (and jointly exaustive, if the model is closed) rules, which can be useful for many purposes.

The keyword argument `force_syntaxtree`, when set to true, causes the logical antecedents in the returned rules to be represented as `SyntaxTree`s, as opposed to other syntax structure (e.g., `LeftmostConjunctiveForm`).

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

```

See also [`listimmediaterules`](@ref), [`SoleLogics.CONJUNCTION`](@ref), [`joinrules`](@ref), [`LeafModel`](@ref), [`AbstractModel`](@ref).
