```
SortedIteratorProduct(by::Function, iterators...)
```

Construct an iterator over the cartesian product of `iterators` that is sorted according to `by`. `by` must be non-decreasing over the indices of `iterators`.

For example, if there are two iterators `a` and `b`, then `by(first(a), first(b)) ≤ by(first(a), second(b))` where `second(b)` is the second element of `b`.

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
