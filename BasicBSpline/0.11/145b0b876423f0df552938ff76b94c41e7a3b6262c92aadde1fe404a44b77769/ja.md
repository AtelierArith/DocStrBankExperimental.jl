インデックスをBスプライン空間のドメイン内の区間に返す

# 例

```jldoctest
julia> k = KnotVector([0.0, 1.5, 2.5, 5.5, 8.0, 9.0, 9.5, 10.0]);


julia> P = BSplineSpace{2}(k);


julia> domain(P)
2.5 .. 9.0

julia> intervalindex(P,2.6)
1

julia> intervalindex(P,5.6)
2

julia> intervalindex(P,8.5)
3

julia> intervalindex(P,9.5)
3
```
