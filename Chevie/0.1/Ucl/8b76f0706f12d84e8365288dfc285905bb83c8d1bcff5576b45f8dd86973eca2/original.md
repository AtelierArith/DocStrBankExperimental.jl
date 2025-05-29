`distinguished_parabolics(W)`

the  list of distinguished (in the  sense of Richardson) standard parabolic subgroups `W_I` of `W`, each given by the list `I` of indices in the simple reflections. The distinguished unipotent conjugacy classes of the reductive group  `𝐆` with Weyl group `W` consist of  the dense unipotent orbit in the unipotent  radical of a  parabolic subgroup `𝐏_I`  of `𝐆` associated with a distinguished  `W_I`.  Their  Dynkin-Richardson  diagram  contains  a  0 at indices  `I` and a 2 in other entries. If `𝐏_I=𝐋𝐔` is a Levi decomposition, `𝐏_I` is distinguished iff `dim 𝐋∩𝐆'=dim 𝐔/𝐔'`.

```julia-repl
julia> W=coxgroup(:F,4)
F₄

julia> distinguished_parabolics(W)
4-element Vector{Vector{Int64}}:
 []
 [3]
 [1, 3]
 [1, 3, 4]
```
