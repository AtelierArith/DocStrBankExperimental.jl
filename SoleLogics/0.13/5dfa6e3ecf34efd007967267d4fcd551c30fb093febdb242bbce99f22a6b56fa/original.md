```
composeformulas(c::Connective, φs::NTuple{N,F})::F where {N,F<:Formula}
```

Return a new formula of type `F` by composing `N` formulas of the same type via a connective `c`. This function allows one to use connectives for flexibly composing formulas (see *Implementation* section).

# Examples

```julia-repl
julia> f = parseformula("◊(p→q)");

julia> p = Atom("p");

julia> ∧(f, p)  # Easy way to compose a formula
SyntaxBranch: ◊(p → q) ∧ p

julia> f ∧ ¬p   # Leverage infix notation ;) (see https://stackoverflow.com/a/60321302/5646732)
SyntaxBranch: ◊(p → q) ∧ ¬p

julia> ∧(f, p, ¬p) # Shortcut for ∧(f, ∧(p, ¬p))
SyntaxBranch: ◊(p → q) ∧ p ∧ ¬p
```

# Implementation

Upon `composeformulas` lies a flexible way of using connectives for composing formulas and syntax tokens (e.g., atoms), given by methods like the following:

```
function (c::Connective)(φs::NTuple{N,Formula}) where {N}
    ...
end
```

These allow composing formulas as in `∧(f, ¬p)`, and in order to access this composition with any newly defined subtype of `Formula`, a new method for `composeformulas` should be defined, together with promotion from/to other `Formula`s should be taken care of (see [here](https://docs.julialang.org/en/v1/manual/conversion-and-promotion/) and [here](https://github.com/JuliaLang/julia/blob/master/base/promotion.jl)).

Similarly, for allowing a (possibly newly defined) connective to be applied on a number of syntax tokens/formulas that differs from its arity, for any newly defined connective `c`, new methods similar to the two above should be defined. For example, although ∧ and ∨ are binary, (i.e., have arity equal to 2), compositions such as `∧(f, f2, f3, ...)` and `∨(f, f2, f3, ...)` can be done thanks to the following two methods that were defined in SoleLogics:

```
function ∧(
    c1::Formula,
    c2::Formula,
    c3::Formula,
    cs::Formula...
)
    return ∧(c1, ∧(c2, c3, cs...))
end
function ∨(
    c1::Formula,
    c2::Formula,
    c3::Formula,
    cs::Formula...
)
    return ∨(c1, ∨(c2, c3, cs...))
end
```

!!! note
    To allow for the composition of `Formula`s of different types, promotion rules should be provided.


See also [`Formula`](@ref), [`Connective`](@ref).
