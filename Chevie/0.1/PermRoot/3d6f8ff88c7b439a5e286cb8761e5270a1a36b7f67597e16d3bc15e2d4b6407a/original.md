`parabolic_reps(W)`

For  a Coxeter group or finite complex reflection group `W`, returns a list of  indices  of  roots  of  `W`  describing  representatives  of  orbits of parabolic  subgroups  under  conjugation  by  `W`. For Coxeter groups, each orbit  has a representative which is a standard parabolic subgroup, that is whose indices is a subset of `eachindex(gens(W))`. This may not be the case in general.

```julia-repl
julia> parabolic_reps(coxgroup(:A,4))
7-element Vector{Vector{Int64}}:
 []
 [1]
 [1, 2]
 [1, 3]
 [1, 2, 3]
 [1, 2, 4]
 [1, 2, 3, 4]

julia> parabolic_reps(complex_reflection_group(3,3,3))
7-element Vector{Vector{Int64}}:
 []
 [1]
 [1, 2]
 [1, 3]
 [1, 9]
 [2, 3]
 [1, 2, 3]
```

`parabolic_reps(W,r)`

If  a second  argument `r`  is given,  returns only  representatives of the parabolic subgroups of semisimple rank `r`.

```julia-repl
julia> parabolic_reps(coxgroup(:A,4),2)
2-element Vector{Vector{Int64}}:
 [1, 2]
 [1, 3]

julia> parabolic_reps(complex_reflection_group(3,3,3),2)
4-element Vector{Vector{Int64}}:
 [1, 2]
 [1, 3]
 [1, 9]
 [2, 3]
```
