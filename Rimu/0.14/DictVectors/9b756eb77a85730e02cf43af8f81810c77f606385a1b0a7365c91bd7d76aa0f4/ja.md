```
InitiatorRule{V}
```

[`InitiatorDVec`](@ref) のためのイニシエータールールを定義するための抽象型。具体的な実装：

  * [`Initiator`](@ref)
  * [`SimpleInitiator`](@ref)
  * [`CoherentInitiator`](@ref)
  * [`NonInitiator`](@ref)

# 拡張ヘルプ

`InitiatorRule` は、関連する [`AbstractInitiatorValue`](@ref) からデータを保存および取得する方法を定義します。新しい `InitiatorRule` を定義する際には、次のことも定義してください：

  * [`initiator_valtype`](@ref)
  * [`from_initiator_value`](@ref)
  * [`to_initiator_value`](@ref)
