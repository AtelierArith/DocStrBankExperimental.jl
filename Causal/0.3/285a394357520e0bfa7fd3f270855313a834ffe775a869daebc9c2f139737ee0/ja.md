```julia
launch(comp)

```

`comp`の`trigger`リンクと`output`バスが駆動可能になるようにタスクのタプルを返します。起動されると、`comp`はその`trigger`リンクから駆動される準備が整います。詳細については、[`drive!(comp::AbstractComponent, t)`](@ref)を参照してください。
