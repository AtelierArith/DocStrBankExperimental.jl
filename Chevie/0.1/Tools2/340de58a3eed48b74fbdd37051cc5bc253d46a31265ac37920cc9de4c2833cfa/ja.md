`factor(p::Mvp)`

`p` は次数 <=2 である必要があり、したがって二次形式を表します。この関数は、`p` がそのような形式の積である場合、2つの線形形式のリストを返します。そうでない場合は、[p] を返します。

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
