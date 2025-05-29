```
fill_in_supports!(model::InfiniteModel; [num_supports::Int = DefaultNumSupports,
                  modify::Bool = true])::Nothing
```

モデル内のすべての無限パラメータに対してサポートポイントを自動的に生成します。これは、モデル内の各パラメータに対して `fill_in_supports!` を呼び出します。詳細については [`fill_in_supports!`](@ref) を参照してください。無限ドメインタイプのいずれかが認識されない場合はエラーが発生します。特定のパラメータにすでにサポートがある場合、`modify = false` の場合はサポートは追加されないことに注意してください。

**例**

```julia-repl
julia> fill_in_supports!(model, num_supports = 4)

julia> supports(t)
4-element Array{Float64,1}:
 0.0
 0.333
 0.667
 1.0
```
