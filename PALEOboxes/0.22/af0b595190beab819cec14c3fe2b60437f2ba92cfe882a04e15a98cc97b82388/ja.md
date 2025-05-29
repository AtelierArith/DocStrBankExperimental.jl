```
add_method_setup!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_setup!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

セットアップメソッドを追加または作成して追加します（メインループの前に呼び出されます）。例えば、永続データを設定したり、状態変数を初期化したりするためです。`methodfn`、`vars`、`kwargs`は[`ReactionMethod`](@ref)に渡されます。
