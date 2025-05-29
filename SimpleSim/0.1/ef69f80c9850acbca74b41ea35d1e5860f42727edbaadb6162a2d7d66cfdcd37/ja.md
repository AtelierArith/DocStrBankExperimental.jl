```
@state model
```

`model`の現在の状態を返します。このマクロは、サブモデルの状態にアクセスする必要がある`fc`または`fd`関数で便利です。このマクロは[`@out`](@ref)と似たように機能します。

**注意:** `@state`は`model`を更新しません。現在の状態を返すだけです。サブモデルを更新するには[`@call!`](@ref)を使用してください。

# 例

```julia
function fc_parent_model(x, u, p, t; models)
    x_child = @state models[1]
    # ...
end
```
