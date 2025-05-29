```
WeightedLex{T,S} <: LexOrdering
WeightedLex(A::Alphabet; weights[, order=collect(A)])
```

単語を最初にその重みで比較し、次に（左）辞書順で同点を解消します。

`weights` ベクトルは、**アルファベットに現れる順に** 各文字に重みを割り当て、単語の重みはそのすべての文字の重みの合計です。

すべての重みが `1` の場合、`WeightedLex` は `LenLex` になります。

# 例

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
