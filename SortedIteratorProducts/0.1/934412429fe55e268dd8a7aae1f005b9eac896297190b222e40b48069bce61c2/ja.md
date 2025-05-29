```
SortedIteratorProduct(by::Function, iterators...)
```

`iterators`の直積に対して`by`に従ってソートされたイテレータを構築します。`by`は`iterators`のインデックスに対して単調非減少でなければなりません。

例えば、2つのイテレータ`a`と`b`がある場合、`by(first(a), first(b)) ≤ by(first(a), second(b))`が成り立ちます。ここで、`second(b)`は`b`の2番目の要素です。

```jldoctest
julia> using ..SortedIteratorProducts, Base.Iterators

julia> A = Iterators.Count(1, 1);

julia> B = Iterators.Count(3, 2);

julia> x = SortedIteratorProduct(sum, A, B);

julia> collect(take(x, 6))
6-element Vector{Tuple{Int64, Int64}}:
 (1, 3)
 (2, 3)
 (3, 3)
 (1, 5)
 (4, 3)
 (2, 5)

julia> x = SortedIteratorProduct(((b,a),) -> b^a, B, A);

julia> collect(take(x, 6))
6-element Vector{Tuple{Int64, Int64}}:
 (3, 1)
 (5, 1)
 (7, 1)
 (9, 1)
 (3, 2)
 (11, 1)
```
