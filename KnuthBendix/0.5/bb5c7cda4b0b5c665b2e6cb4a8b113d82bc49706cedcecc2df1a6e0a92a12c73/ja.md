```
LenLex{T} <: LexOrdering
LenLex(A::Alphabet[; order=collect(A)])
```

単語をまずその長さで比較し、次に（左）辞書順で同点を解消します。

# 例

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
