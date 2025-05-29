```julia
drive!(comp, t)

```

`t`を`comp`の`trigger`リンクに書き込みます。駆動されると、`comp`はステップを踏みます。参照: [`takestep!(comp::AbstractComponent)`](@ref)
