```
add_method_do!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_do!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

メインループメソッドを追加または作成して追加します。 `methodfn`、`vars`、`kwargs`は[`ReactionMethod`](@ref)に渡されます。
