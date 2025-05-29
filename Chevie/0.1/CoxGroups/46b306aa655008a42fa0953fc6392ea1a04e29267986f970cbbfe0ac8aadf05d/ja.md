`bruhatless(W, x, y)`

`x≤y` が Bruhat 順序で成り立つかどうかを判定します。ここで `x,y∈ W` です。`x≤y` であるためには、`x` の縮約表現が `w` のものから抽出できる必要があります。Bruhat 順序の性質については [(5.9) と (5.10) Humphreys1990](biblio.htm#Hum90) を参照してください。

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> w=W(1,2,1,3);

julia> b=filter(x->bruhatless(W,x,w),elements(W));

julia> word.(Ref(W),b)
12-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [3]
 [1, 2]
 [2, 1]
 [1, 3]
 [2, 3]
 [1, 2, 1]
 [1, 2, 3]
 [2, 1, 3]
 [1, 2, 1, 3]
```
