与えられた `Tableau` `t` と同じ数のキュービットを持ち、`t` のすべての演算子と可換なすべてのパウリ演算子を返します。

```jldoctest
julia> normalizer(T"X")
+ _
+ X
```
