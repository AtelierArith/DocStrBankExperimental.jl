```
optimize!(
    model::GenericModel;
    ignore_optimize_hook = (model.optimize_hook === nothing),
    kwargs...,
)

モデルを最適化します。

まだオプティマイザーが設定されていない場合（[`set_optimizer`](@ref)を参照）、[`NoOptimizer`](@ref)エラーがスローされます。

`ignore_optimize_hook == true`の場合、最適化フックは無視され、フックが設定されていないかのようにモデルが解決されます。キーワード引数`kwargs`は`optimize_hook`に渡されます。`optimize_hook`が`nothing`であり、キーワード引数が提供された場合、エラーがスローされます。

## 例

```

jldoctest julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> function my*optimize*hook(model; foo)            println("Hook called with foo = ", foo)            return optimize!(model; ignore*optimize*hook = true)        end my*optimize*hook (generic function with 1 method)

julia> set*optimize*hook(model, my*optimize*hook) my*optimize*hook (generic function with 1 method)

julia> optimize!(model; foo = 2) Hook called with foo = 2 ```
