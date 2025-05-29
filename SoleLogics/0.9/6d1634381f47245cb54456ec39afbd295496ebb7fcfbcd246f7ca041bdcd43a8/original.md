```
abstract type Connective <: Syntactical end
```

Abstract type for [logical connectives](https://en.wikipedia.org/wiki/Logical_connective), that are used to express non-atomic statements; for example, CONJUNCTION, DISJUNCTION, NEGATION and IMPLICATION (stylized as ∧, ∨, ¬ and →).

# Implementation

When implementing a new type `C` for a connective, please define its `arity`. For example, with a binary operator (e.g., ∨ or ∧):

```
arity(::C) = 2
```

When implementing a new type `C` for a *commutative* connective with arity higher than 1, please provide a method `iscommutative(::C)`. This can speed up model checking operations.

When implementing a custom binary connective, one can override the default `precedence` and `associativity` (see [here](https://docs.julialang.org/en/v1/manual/mathematical-operations/#Operator-Precedence-and-Associativity). If the custom connective is a `NamedConnective` and renders as something considered as a `math symbol` (for example, `⊙`, see https://stackoverflow.com/a/60321302/5646732), by the Julia parser, `Base.operator_precedence` and `Base.operator_associativity` are used to define these behaviors, and you might want to avoid providing these methods at all.

The semantics of a *propositional* connective can be specified via `collatetruth` (see example below); in principle, the definition can rely on the partial order between truth values (specified via `precedes`).

Here is an example of a custom implementation of the xor (⊻) Boolean operator.

```julia
import SoleLogics: arity, iscommutative, collatetruth
const ⊻ = SoleLogics.NamedConnective{:⊻}()
SoleLogics.arity(::typeof(⊻)) = 2
SoleLogics.iscommutative(::typeof(⊻)) = true
SoleLogics.collatetruth(::typeof(⊻), (t1, t2)::NTuple{N,T where T<:BooleanTruth}) where {N} = (count(istop, (t1, t2)) == 1)
```

Note that `collatetruth` must be defined at least for some truth value types `T` via methods accepting an `NTuple{arity,T}` as a second argument.

To make the operator work with incomplete interpretations (e.g., when the `Truth` value for an atom is not known), simplification rules for `NTuple{arity,T where T<:Formula}`s should be provided via methods for `simplify`. For example, these rules suffice for simplifying xors between `TOP/`BOT`s, and other formulas:

```julia
import SoleLogics: simplify
simplify(::typeof(⊻), (t1, t2)::Tuple{BooleanTruth,BooleanTruth}) = istop(t1) == istop(t2) ? BOT : TOP
simplify(::typeof(⊻), (t1, t2)::Tuple{BooleanTruth,Formula}) = istop(t1) ? ¬t2 : t2
simplify(::typeof(⊻), (t1, t2)::Tuple{Formula,BooleanTruth}) = istop(t2) ? ¬t1 : t1
```

Beware of dispatch ambiguities!

See also [`arity`](@ref), [`SyntaxBranch`](@ref), [`associativity`](@ref), [`precedence`](@ref), [`check`](@ref), [`iscommutative`](@ref), [`NamedConnective`](@ref), [`Syntactical`](@ref).
