```
LenLex{T} <: LexOrdering
LenLex(A::Alphabet[; order=collect(A)])
```

Compare words first by their length, then break ties by (left-)lexicographic order.

# Example

```jldoctest
julia> Al = Alphabet([:a, :A, :b, :B]);

julia> ll1 = LenLex(Al)
LenLex: a < A < b < B

julia> ll2 = LenLex(Al, order=[:a, :b, :A, :B])
LenLex: a < b < A < B

julia> a, A, b, B = [Word([i]) for i in 1:length(Al)];

julia> lt(ll1, a*A, a*b)
true

julia> lt(ll2, a*A, a*b)
false
```
