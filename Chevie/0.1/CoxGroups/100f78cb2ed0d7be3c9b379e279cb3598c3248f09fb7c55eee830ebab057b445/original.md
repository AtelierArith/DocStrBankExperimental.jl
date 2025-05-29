`coxeter_symmetric_group(n::Integer)` or `coxeter_symmetric_group(m:n)` or `coxsym(n)` or `coxsym(m:n)`

The  symmetric group on the  letters `1:n` (or if  a `m≤n` is given, on the letters  `m:n`)  as  a  Coxeter  group.  The  Coxeter  generators  are  the `Perm(i,i+1)` for `i` in `m:n-1`.

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> gens(W)
2-element Vector{Perm{Int16}}:
 (1,2)
 (2,3)

julia> e=elements(W)
6-element Vector{Perm{Int16}}:
 ()
 (1,2)
 (2,3)
 (1,3,2)
 (1,2,3)
 (1,3)

julia> length.(Ref(W),e) # length in the genrators of the elements
6-element Vector{Int64}:
 0
 1
 1
 2
 2
 3
```
