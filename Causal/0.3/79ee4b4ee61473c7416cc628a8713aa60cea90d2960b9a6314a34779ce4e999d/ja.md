```julia
takestep!(comp)

```

`comp`の`trigger`リンクから時間`t`を読み取ります。`comp`が`AbstractMemory`の場合、後方ステップが実行されます。それ以外の場合は、前方ステップが実行されます。詳細については、[`forwardstep`](@ref)、[`backwardstep`](@ref)を参照してください。
