```
JuMP.optimize!(model::InfiniteModel; [kwargs...])
```

`JuMP.optimize!`を拡張して、内部最適化モデルを使用して無限モデルを最適化します。最適化モデルが最新でない場合は、[`build_optimizer_model!`](@ref)が呼び出されます。`kwargs`は、定義されている場合に[`build_optimizer_model!`](@ref)に渡されるキーワード引数に対応します。

**例**

```julia-repl
julia> optimize!(model)

julia> has_values(model)
true
```
