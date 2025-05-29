`moebius(P::CPoset,y=first(maxima(P)))`

値のベクトル `μ(x,y)` は、`P` のモービウス関数のもので、`x` が変化します。以下は、整数に対する通常のモービウス関数を示す例です。

```julia-repl
julia> p=CPoset((i,j)->i%j==0,8)
5,7<1
6<2<1
6<3<1
8<4<2

julia> moebius(p)
8-element Vector{Int64}:
  1
 -1
 -1
  0
 -1
  1
 -1
  0
```
