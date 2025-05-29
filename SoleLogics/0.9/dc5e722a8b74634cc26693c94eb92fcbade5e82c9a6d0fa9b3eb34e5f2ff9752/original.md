```
normalize(
    f::Formula;
    profile = :readability,
    remove_boxes = nothing,
    reduce_negations = true,
    simplify_constants = true,
    allow_atom_flipping = false,
    prefer_implications = false,
    remove_implications = false,
    forced_negation_removal = nothing,
    remove_identities = true,
    unify_toones = true,
    rotate_commutatives = true,
)
```

Return a modified version of a given formula, that has the same semantics but different syntax. This is useful for simplifying formulas for readability, or when checking the truth of many (possibly semantically similar) formulas; for example, when performing [model checking](https://en.wikipedia.org/wiki/Model_checking). The current implementation assumes the underlying algebra is Boolean!

# Arguments

  * `f::Formula`: when set to `true`,   the formula;
  * `profile::Symbol`: possible values are :readability, which optimizes for qualitative   simplicity for a human to understand, and :modelchecking, which optimizes   model checking speed;
  * `remove_boxes::Bool`: remove all (non-relational and relational) box operators by using the   equivalence ◊φ ≡ ¬□¬φ. Note: this assumes an underlying Boolean algebra.
  * `reduce_negations::Bool`: when set to `true`,   attempts at reducing the number of negations by appling   some transformation rules   (e.g., [De Morgan's laws](https://en.wikipedia.org/wiki/De_Morgan%27s_laws)).   Note: this assumes an underlying Boolean algebra.
  * `allow_atom_flipping::Bool`: when set to `true`,   together with `reduce_negations=true`, this may cause the negation of an atom   to be replaced with the its [`dual`](@ref) atom.

# Examples

```julia-repl
julia> f = parseformula("□¬((p∧¬q)→r)∧⊤");

julia> syntaxstring(f)
"□¬((p ∧ ¬q) → r) ∧ ⊤"

julia> syntaxstring(SoleLogics.normalize(f; profile = :modelchecking, allow_atom_flipping = false))
"¬◊(q ∨ ¬p ∨ r)"

julia> syntaxstring(SoleLogics.normalize(f; profile = :readability, allow_atom_flipping = false))
"□(¬r ∧ p ∧ ¬q)"
```

See also [`SyntaxTree`](@ref)), [`Formula`](@ref).
