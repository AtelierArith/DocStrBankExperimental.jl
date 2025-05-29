```
normalize(::Union{typeof(¬), typeof(∧), typeof(∨)}, p)
```

Convert the given proposition to negation, conjunction, or disjunction normal form depending on whether the first argument is [`not`](@ref), [`and`](@ref), or [`or`](@ref), respectively.

Considering the syntax tree of a normalized proposition, each leaf node is a literal; either an atom or it's negation. Propositions in negation normal form are expanded such that the syntax tree branches only contain the operators `and` and `or`. Conjunction and disjunction normal forms are negated normal forms that have been flattened by recursively distributing either the `and` or `or` operator over the other. In other words, a collection of literals is a clause and a proposition in conjunctive or disjunctive normal form is a conjunction of disjunctive clauses or a disjunction of conjunctive clauses, respectively.

Conjunction and disjunction, but not negation, normal forms are called *canonical*. Distributing an operator during conversion may increase the size of the syntax tree exponentially. Therefore, it may be intractable to compute a canonical form for sufficiently large propositions. Instead, use the [`tseytin`](@ref) transformation to find a proposition in conjunctive normal form which [`is_equisatisfiable`](@ref) to the given proposition.

!!! tip
    Converting a proposition between conjunction and disjunction normal form is not performant due to the exponential increase in the size of the proposition. It is most performant to apply all operations to propositions and normalizing the resulting proposition once.


# Examples

```jldoctest
julia> @atomize normalize(∧, ¬(p ∨ q))
(¬p) ∧ (¬q)

julia> @atomize normalize(∨, p ↔ q)
(¬q ∧ ¬p) ∨ (q ∧ p)
```
