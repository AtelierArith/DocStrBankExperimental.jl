```
union_bases(a::Projection,b::Projection,args...) -> Projection
```

Computes the projection corresponding to the union of `a` and `b`. In essence this operation performs as

`gram_schmidt(union(get_basis(a),get_basis(b)))`
