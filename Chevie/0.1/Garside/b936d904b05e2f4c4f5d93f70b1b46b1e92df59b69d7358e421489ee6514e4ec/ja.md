`CorranPicantinMonoid(e,n,k=1)`

は、G. Neaimeによって定義された区間モノイドを返します。http://arxiv.org/abs/1707.06864 これは、`G(e,e,n)`のためのCorran-Picantinモノイドを一般化しています。

このモノイドにおいて、`δ`の`image`は、対角行列の要素で、最初の要素を除く対角成分が`E(e)^k`に等しい`G(e,e,n)`に対応します。このモノイドは、`gcd(k,e)=1`のときに`G(e,e,n)`のためのCorran-Picantinモノイドと同型です。

```julia-repl
julia> C=CorranPicantinMonoid(3,3)
CorranPicantinMonoid(3,3,3)

julia> word(C(C.δ))
6-element Vector{Int64}:
 1
 3
 4
 1
 3
 4

julia> Matrix(C,C.δ)
3×3 Matrix{Cyc{Int64}}:
 ζ₃   0   0
  0  ζ₃   0
  0   0  ζ₃

julia> b=C(1,2,3,4)^3
1.2.341.2.341.2.34

julia> Matrix(C,b[3])
3×3 Matrix{Cyc{Int64}}:
 0    0  ζ₃
 0  ζ₃²   0
 1    0   0
```

© 2017年7月 –- ジャン・ミッシェルとジョルジュ・ネアイム
