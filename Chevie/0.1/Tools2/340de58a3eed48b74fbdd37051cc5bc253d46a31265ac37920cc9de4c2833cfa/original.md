`factor(p::Mvp)`

`p`  should be of degree <=2 thus  represent a quadratic form. The function returns  a list  of two  linear forms  of which  `p` is the product if such forms exist, otherwise it returns [p].

```julia-repl
julia> @Mvp x,y

julia> factor(x^2-y^2+x+3y-2)
2-element Vector{Mvp{Int64, Int64}}:
 x-y+2
 x+y-1

julia> factor(x^2+x+1)
2-element Vector{Mvp{Cyc{Int64}, Int64}}:
 x-ζ₃
 x-ζ₃²

julia> factor(x*y-1)
1-element Vector{Mvp{Int64, Int64}}:
 xy-1
```
