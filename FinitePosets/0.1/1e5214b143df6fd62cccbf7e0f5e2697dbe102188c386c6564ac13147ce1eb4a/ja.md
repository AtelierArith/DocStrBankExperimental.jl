`transitive_closure(M)` `transitive_closure!(M)`

`M` は関係を表す正方形のブール行列であるべきです。`transitive_closure` はこの関係の推移閉包を表すブール行列を返します。`transitive_closure!` は `M` をその場で変更し、アロケーションを行いません。推移閉包はフロイド・ワーシャルアルゴリズムによって計算され、これは大きな行列に対しても非常に高速です。

```julia-repl
julia> m=[j-i in [0,1] for i in 1:5, j in 1:5]
5×5 Matrix{Bool}:
 1  1  0  0  0
 0  1  1  0  0
 0  0  1  1  0
 0  0  0  1  1
 0  0  0  0  1

julia> transitive_closure(m)
5×5 Matrix{Bool}:
 1  1  1  1  1
 0  1  1  1  1
 0  0  1  1  1
 0  0  0  1  1
 0  0  0  0  1
```
