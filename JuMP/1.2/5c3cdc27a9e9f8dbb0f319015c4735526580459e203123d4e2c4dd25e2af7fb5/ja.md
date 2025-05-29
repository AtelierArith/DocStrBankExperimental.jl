```
set_optimize_hook(model::Model, f::Union{Function,Nothing})
```

`f`を`model`の最適化フックとして設定します。

`f`は`f(model::Model; kwargs...)`というシグネチャを持つ必要があり、`kwargs`は[`optimize!`](@ref)に渡されるものです。

## 注意事項

  * 最適化フックは一般的にモデルや外部の状態を何らかの方法で変更し、その後`optimize!(model; ignore_optimize_hook = true)`を呼び出してフックをバイパスしながら問題を最適化する必要があります。
  * 最適化フックを解除するには`set_optimize_hook(model, nothing)`を使用します。

## 例

```julia
model = Model()
function my_hook(model::Model; kwargs...)
    print(kwargs)
    return optimize!(model; ignore_optimize_hook = true)
end
set_optimize_hook(model, my_hook)
optimize!(model; test_arg = true)
```
