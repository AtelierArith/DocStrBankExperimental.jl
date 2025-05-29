```
WeightedLex{T,S} <: LexOrdering
WeightedLex(A::Alphabet; weights[, order=collect(A)])
```

Compare words first by their weight, then break ties by (left-)lexicographic order.

The `weights` vector assigns weights to each letter **as they appear in the alphabet** and the weight of a word is the sum of weights of all of its letters.

With all weights equal to `1` `WeightedLex` becomes `LenLex`.

# Example

```jldoctest
julia> al = Alphabet([:a, :A, :b, :B]);

julia> a, A, b, B = (Word([i]) for i in 1:length(al));

julia> wtlex = WeightedLex(al, weights=[1, 2, 3, 4], order=[:a, :b, :B, :A])
WeightedLex: a(1) < b(3) < B(4) < A(2)

julia> lt(wtlex, b * B, B * a * a * a)
true

julia> lt(wtlex, A*B, B*A)
false
```
