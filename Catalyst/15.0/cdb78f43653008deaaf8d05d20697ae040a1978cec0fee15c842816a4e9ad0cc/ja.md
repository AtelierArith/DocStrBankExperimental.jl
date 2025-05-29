```
ModelingToolkit.extend(sys::AbstractSystem, rs::ReactionSystem; name::Symbol=nameof(sys))
```

指定された[`ReactionSystem`](@ref)を別の`AbstractSystem`で拡張します。

注意:

  * 追加される`AbstractSystem`は、現在`ODESystem`、`NonlinearSystem`、または`ReactionSystem`でなければなりません。
  * 新しい`ReactionSystem`を返し、`rs`は変更しません。
  * デフォルトでは、新しい`ReactionSystem`は`sys`と同じ名前になります。
