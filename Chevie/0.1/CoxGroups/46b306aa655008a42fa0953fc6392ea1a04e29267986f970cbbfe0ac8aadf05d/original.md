`bruhatless(W, x, y)`

whether `x≤y` in the Bruhat order, for `x,y∈ W`. We have `x≤y` if a reduced expression for `x` can be extracted from one for `w`. See [(5.9) and (5.10) Humphreys1990](biblio.htm#Hum90) for properties of the Bruhat order.

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
