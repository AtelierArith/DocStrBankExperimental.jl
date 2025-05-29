```
inner_product(L::AbstractLat, v::Vector, w::Vector) -> FieldElem
```

ベクトル `v` と `w` の内積を `rational_span(L)` の双線形形式に関して返します。$L$ が自由であり、$G$ がそのグラム行列である場合、これは $v G w^t$ です。
