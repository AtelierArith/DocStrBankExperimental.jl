```
fold(f, pairs...)
```

A generalization of `mapreduce` with an arbitrary number of nested folds and traits to determine each operator's [`Associativity`](@ref Interface.Associativity) and [`initial_value`](@ref Interface.initial_value).

The function `f` must accept as many parameters as there are `pairs`. Each pair must be a two element iterable where the first element is a binary operator and the second element is an iterable to be folded over.

Given a single pair, this function is similar to `mapreduce` and other similar functions. Giving additional pairs will generalize the following pattern:

```julia
mapreduce(a, xs) do x
    mapreduce(b, ys) do y
        ...
    end
end
```

This can be rewritten as:

```julia
fold(a => xs, b => ys, ...) do x, y, ...
    ...
end
```

# Examples

```jldoctest
julia> fold(⊤)
⊤

julia> @atomize fold(¬, (∧) => (p, q))
¬p ∧ ¬q

julia> @atomize fold(↔, (∧) => (p, q), (∨) => (r, s))
((p ↔ r) ∨ (p ↔ s)) ∧ ((q ↔ r) ∨ (q ↔ s))
```
