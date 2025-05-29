```
PriorityChannel{T}(sz::Int)
```

`sz`の型`T`のオブジェクトを最大`sz`個保持できる内部バッファを持つ`PriorityChannel`を構築します。各オブジェクトには実数値の優先度が割り当てられます（低い数値 = 高い優先度）。満杯のチャネルでの[`put!`](@ref)呼び出しは、[`take!`](@ref)でオブジェクトが削除されるまでブロックされます。

`PriorityChannel(0)`はバッファなしのチャネルを構築します。`put!`は対応する`take!`が呼ばれるまでブロックされます。そしてその逆も同様です。

他のコンストラクタ:

  * `PriorityChannel(Inf)`: `PriorityChannel{Any,Int}(typemax(Int))`と同等
  * `PriorityChannel(sz)`: `PriorityChannel{Any,Int}(sz)`と同等
