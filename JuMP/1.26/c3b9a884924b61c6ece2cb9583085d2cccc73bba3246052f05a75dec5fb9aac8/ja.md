```
set_optimize_hook(model::GenericModel, f::Union{Function,Nothing})
```

`f`を`model`の最適化フックとして設定します。

`f`は`f(model::GenericModel; kwargs...)`というシグネチャを持つ必要があり、`kwargs`は[`optimize!`](@ref)に渡されるものです。

## 注意事項

  * 最適化フックは一般的にモデルや外部の状態を何らかの方法で変更し、その後`optimize!(model; ignore_optimize_hook = true)`を呼び出してフックをバイパスしながら問題を最適化する必要があります。
  * 最適化フックを解除するには`set_optimize_hook(model, nothing)`を使用します。

## 例

```jldoctest
julia> model = Model();

julia> function my_hook(model::Model; kwargs...)
           println(kwargs)
           println("Calling with `ignore_optimize_hook = true`")
           optimize!(model; ignore_optimize_hook = true)
           return
       end
my_hook (generic function with 1 method)

julia> set_optimize_hook(model, my_hook)
my_hook (generic function with 1 method)

julia> optimize!(model; test_arg = true)
Base.Pairs{Symbol, Bool, Tuple{Symbol}, @NamedTuple{test_arg::Bool}}(:test_arg => 1)
Calling with `ignore_optimize_hook = true`
ERROR: NoOptimizer()
[...]
```
