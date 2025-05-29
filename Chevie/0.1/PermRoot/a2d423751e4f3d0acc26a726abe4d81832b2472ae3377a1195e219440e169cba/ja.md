`bipartite_decomposition(W)`

反射群 `W` の生成子のインデックスの二部分解 `[L,R]` を返します。ここで、`reflection_subgroup(W,L)` と `reflection_subgroup(W,R)` はアーベル部分群であり、`W=reflection_subgroup(W, vcat(L,R))` です。このような分解が不可能な場合はエラーを返します。

```julia-repl
julia> bipartite_decomposition(coxgroup(:E,8))
([1, 4, 6, 8], [3, 2, 5, 7])

```
