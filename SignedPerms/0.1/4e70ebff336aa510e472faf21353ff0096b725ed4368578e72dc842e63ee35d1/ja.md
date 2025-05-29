`invpermute(l::AbstractVector,p::SPerm)`

は、`l`を`p`で逆順に並べ替えた結果を返します。これは、`r`というベクトルであり、`r[abs(i^p)]=l[i]*sign(i^p)`となります。

```julia-repl
julia> p=SPerm([-2,-1,-3])
SPerm{Int64}: (1,-2)(3,-3)

julia> invpermute([20,30,40],p)
3-element Vector{Int64}:
 -30
 -20
 -40
```

`invpermute`は、キーワード`dims`を使って行列にも作用します。`dims=1`の場合は行を逆順に並べ替え、`dims=2`の場合は列を逆順に並べ替え、`dims=(1,2)`の場合は両方を逆順に並べ替えます。もし`P=Matrix(p)`および`iP=Matrix(inv(p))`とすると、`invpermute(m,p;dims=1)==iP*m`、`invpermute(m,p;dims=2)==m*P`、および`invpermute(m,p;dims=(1,2))==iP*m*P`が成り立ちます。最後に、`invpermute(m,p1,p2)`の形は、`m`の行を`p1`で、列を`p2`で逆順に並べ替えます。
