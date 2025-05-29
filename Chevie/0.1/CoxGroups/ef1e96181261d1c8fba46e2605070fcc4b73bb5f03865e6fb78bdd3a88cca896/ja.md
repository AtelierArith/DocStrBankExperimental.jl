`inversions(W,w)`

有限コクセター群 `W` の要素 `w` の逆転を返します。つまり、`l(rw)<l(w)` となる `W` の反射 `r` のインデックスのリストです。ここで `l` はコクセター長です。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> inversions(W,W(1,2,1))
3-element Vector{Int64}:
 1
 2
 4
```
