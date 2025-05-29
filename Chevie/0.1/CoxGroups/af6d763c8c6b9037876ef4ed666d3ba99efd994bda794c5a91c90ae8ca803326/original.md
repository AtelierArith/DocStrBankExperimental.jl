`bruhatless(W, y)`

returns  a vector  whose `i`-th  element is  the vector  of elements of `W` smaller for the Bruhat order than `w` and of Coxeter length `i-1`. Thus the first  element  of  the  returned  list  contains  only  `one(W)`  and  the `length(W,w)`-th element contains only `w`.

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> bruhatless(W,Perm(1,3))
4-element Vector{Vector{Perm{Int16}}}:
 [()]
 [(1,2), (2,3)]
 [(1,2,3), (1,3,2)]
 [(1,3)]
```

see also [`bruhatPoset`](@ref) for Coxeter groups.
