`Perm{T}(m::AbstractMatrix,m1::AbstractMatrix;dims=1)`

returns  `p`, a `Perm{T}`, which invpermutes the  rows of `m1` (the columns of `m1`  if `dims=2`, simultaneously the rows  and columns if `dims=(1,2)`) to bring  them  to  those  of  `m`,  if  such  a `p` exists; returns `nothing` otherwise.  If not given `{T}` is taken to be `{Int16}`. Needs the elements of `m` and `m1` to be sortable.

```julia-repl
julia> Perm([0 1 0;0 0 1;1 0 0],[1 0 0;0 1 0;0 0 1];dims=1)
(1,3,2)

julia> Perm([0 1 0;0 0 1;1 0 0],[1 0 0;0 1 0;0 0 1];dims=2)
(1,2,3)

julia> n=(1:30)'.*(1:30).%15;

julia> m=onmats(n,Perm(1,5,2,8,12,4,7)*Perm(3,9,11,6));

julia> Perm(m,n,dims=(1,2))
(1,5,2,8,12,4,7)(3,9,11,6)
```
