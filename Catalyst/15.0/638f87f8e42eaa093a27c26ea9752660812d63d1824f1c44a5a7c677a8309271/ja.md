```
species(network)
```

[`ReactionSystem`](@ref) が与えられた場合、システム内および `ReactionSystem` 型のサブシステム内で定義されたすべての種のベクトルを返します。システムおよびすべてのサブシステム内の種および非種変数を取得するには、非 `ReactionSystem` サブシステムを含めて `unknowns(network)` を使用します。

注意:

  * `ModelingToolkit.get_systems(network)` が空でない場合、メモリを割り当てます。
