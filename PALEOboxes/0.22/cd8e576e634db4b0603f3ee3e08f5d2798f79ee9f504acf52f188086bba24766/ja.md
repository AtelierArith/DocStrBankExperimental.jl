```
add_method_initialize!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_initialize!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

初期化メソッドを追加または作成して追加します（各メインループの反復の開始時に呼び出されます）。例えば、累積変数をゼロにするためです。`methodfn`、`vars`、`kwargs`は[`ReactionMethod`](@ref)に渡されます。
