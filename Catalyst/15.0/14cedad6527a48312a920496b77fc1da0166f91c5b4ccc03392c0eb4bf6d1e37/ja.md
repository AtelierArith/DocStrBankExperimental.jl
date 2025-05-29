```
ModelingToolkit.compose(sys::ReactionSystem, systems::AbstractArray; name = nameof(sys))
```

指定された[`ReactionSystem`](@ref)を1つ以上の`AbstractSystem`と組み合わせます。

注意:

  * 追加される`AbstractSystem`は、現在`ODESystem`、`NonlinearSystem`、または`ReactionSystem`である必要があります。
  * 新しい`ReactionSystem`を返し、`rs`は変更しません。
  * デフォルトでは、新しい`ReactionSystem`は`sys`と同じ名前になります。
