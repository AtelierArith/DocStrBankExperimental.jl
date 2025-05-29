```
customtype(stack::PluginStack, typename::Symbol, abstract_type::Type, target_module::Module = Main; unique_name = true)
```

スタック内のプラグインによって提供されたフィールドを持つ型を組み立てます。

`abstract_type` は組み立てられた型のスーパタイプになります。

`unique_name` が `true` の場合、`typename` は構造に依存するIDでサフィックスされます。このIDは評価された式のハッシュとして生成されます（名前の代わりに :TYPE_NAME プレースホルダーが使用されます）。つまり、同じプラグインと同じソースコードがロードされると、同じ型に対して同じIDが生成されます。

# 例

`AppStateImpl <: AppState` 型を組み立て、それを使ってアプリをパラメータ化します。

```julia
abstract type AppState end

mutable struct CustomFieldsApp{TCustomState}
    state::TCustomState
    function CustomFieldsApp(plugins, hookfns, stateargs...)
        stack = PluginStack(plugins, hookfns)
        state_type = customtype(stack, :AppStateImpl, AppState)
        return new{state_type}(Base.invokelatest(state_type, stateargs...))
    end
end
```

!!! note "`invokelatest` の必要性"
    新しく生成された型をインスタンス化するためには `invokelatest` を使用する必要があります。生成された型を通常通り使用するには、型が生成された後に制御フローをトップレベルスコープに戻す必要があります。詳細は [docs](https://docs.julialang.org/en/v1/manual/methods/#Redefining-Methods) を参照してください。


!!! warning "アンチパターン"
    ステート型を組み立てることはアンチパターンです。なぜなら、プラグインは独自のステートを持つことができるからです。（ただし、いくつかのケースではパフォーマンスが向上する可能性があります）組み立てられた型はコードの可読性を低下させる可能性があるため、慎重に使用してください！

