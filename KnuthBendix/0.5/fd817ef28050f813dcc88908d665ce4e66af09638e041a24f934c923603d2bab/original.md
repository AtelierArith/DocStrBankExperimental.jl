```
Recursive{Side,T} <: RewritingOrdering
Recursive{Side}(A::Alphabet; order=collect(A))
```

A special case of `WreathOrder` where each letter is given a unique level.

Since levels are unique they just linearly order letters in the alphabet `A`. The order generally promotes smaller generators, and larger ones will occur in minimal words relatively early. For example if `a < b` then `a·b > b·aⁿ`.

# Definition

Given a partial order `(A, <)` on an alphabet `A`, for `p, q ∈ A*` we say that `p < q` w.r.t. left-recursive ordering if

> 1. `p == ε ≠ q`, or
> 2. `p = p′·a`, `q = q′·b` for some `a, b ∈ A` and
>
>       * `a == b` and `p′ < q′`, or
>       * `a < b` and `p < q′`, or
>       * `a > b` and `p′ < q`


For the right-recursive ordering one needs to change the decompositions in point 2. to

> `p = a·p′`, `q = b·q′` for some `a, b ∈ A` …


For more details consult

> M. Jentzen *Confluent String Rewriting*, Definition 1.2.14 p.24.


The ordering is sometimes also known as *recursive path ordering* and is useful e.g. for polycyclic groups.

# Example

```jldoctest
julia> X = Alphabet([:b, :a, :A],[0, 3, 2]);

julia> b, a, A = [Word([i]) for i in 1:length(X)];

julia> rec = Recursive(X, order=[:a, :A, :b])
KnuthBendix.Left-Recursive: a < A < b

julia> lt(rec, b*a^10, a*b)
true

julia> lt(rec, b*a^10, b)
false

julia> lt(rec, a*A, b*a^10)
true

julia> rt_rec = Recursive{KnuthBendix.Right}(X, order=[:a, :A, :b])
KnuthBendix.Right-Recursive: a < A < b
```
