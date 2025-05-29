```
union_bases(a::Projection,b::Projection,args...) -> Projection
```

`a` と `b` の和集合に対応する射影を計算します。本質的に、この操作は次のように機能します。

`gram_schmidt(union(get_basis(a),get_basis(b)))`
