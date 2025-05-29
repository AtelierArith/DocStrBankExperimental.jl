```
@out model
```

現在の `model` の出力を返します。このマクロは、サブモデルの出力にアクセスする必要がある `fc` または `fd` 関数で便利です。このマクロは [`@state`](@ref) と似たように機能します。

# 例

```julia
function fc_parent_model(x, u, p, t; models)
    y_child = @out models[1]
    # ...
end
```

**注意:** `@out` は `model` を更新しません。現在の出力を返すだけです。サブモデルを更新するには [`@call!`](@ref) を使用してください。
