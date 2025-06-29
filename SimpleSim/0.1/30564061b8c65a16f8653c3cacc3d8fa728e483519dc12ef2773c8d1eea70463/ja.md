```
@call! model u
```

`@call!` マクロは、サブモデルを使用したシミュレーションを実行するために重要です。親モデルの `gc` または `gd` 関数内では、そのすべてのサブモデルを `@call!` を使用して呼び出す必要があります。そうしないと、サブモデルは更新されません。

更新後の `model` の出力を返します。`@call!` を呼び出した後に [`@state`](@ref) を使用して新しい状態にアクセスします。

# 例

```julia
function gc_parent_model(x, u, p, t; models)
    # ...
    y_child = @call! models[1] u_child
    # ...
end
```

*注意:* `@call!` はダイナミクス (`fc` / `fd`) 関数内で使用してはいけません。これによりエラーが発生します。親モデルのダイナミクス関数内でサブモデルの出力/状態にアクセスする必要がある場合は、[`@out`](@ref) / [`@state`](@ref) を使用してください。
