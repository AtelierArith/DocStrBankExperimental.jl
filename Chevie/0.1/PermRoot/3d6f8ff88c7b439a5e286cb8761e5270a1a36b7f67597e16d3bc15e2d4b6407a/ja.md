`parabolic_reps(W)`

コクセター群または有限複素反射群 `W` に対して、`W` による共役の下での放物型部分群の軌道の代表を記述する根のインデックスのリストを返します。コクセター群の場合、各軌道には標準的な放物型部分群の代表があり、そのインデックスは `gens(W)` の `eachindex` の部分集合です。一般にはそうでない場合もあります。

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

第二の引数 `r` が与えられた場合、半単純階数 `r` の放物型部分群の代表のみを返します。

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
