```
HomalgColumnVector(L, r, R)
```

Construct a (r x 1)-matrix over the ring R with entries in the list L, where r = length(L)

```jldoctest
julia> mat = HomalgColumnVector(1:5, ZZ)
[1]
[2]
[3]
[4]
[5]
```
