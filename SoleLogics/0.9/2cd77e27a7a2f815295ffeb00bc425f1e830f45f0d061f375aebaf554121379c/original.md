```
@synexpr(expression)
```

Return an expression after automatically instantiating undefined [`Atom`](@ref)s.

!!! info



All atoms are parsed as `Atom{String}` objects.

!!! warning



The Julia parser can parse some (infix) `NamedConnective`s such as ∧, →, but has a few limitations, including:

  * inexact precedence and associativity for some operators (e.g.,   in fact, as of Julia 1.9, despite `(@synexpr ¬ p ∧ q) == @synexpr ¬(p) ∧ q`,   Base.operator*precedence(:(¬)) < Base.operator*precedence(:(∧)));
  * inability to parse most multi-character, custom-made `Connective`s (e.g., ⟨=⟩, [G]);

For a more flexible parsing, consider using `parseformula`.

# Examples

```julia-repl
julia> @synexpr x = p # Atom{String}("p") is assigned to the global variable x
Atom{String}("p")

julia> @synexpr st = p ∧ q → r
(p ∧ q) → r

julia> token(st)
→
```

See also [`parseformula`](@ref), [`Atom`](@ref), [`Connective`](@ref), [`precedence`](@ref), [`associativity`](@ref).
