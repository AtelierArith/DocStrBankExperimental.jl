```
DebugSolverState <: AbstractManoptSolverState
```

デバッグ状態は、任意の状態にデバッグを追加し、デコレーターパターンとして機能します。内部では、`Symbol`を参照として使用して、いくつかの機会のために[`DebugAction`](@ref)を格納する辞書が保持されます。

元のオプションには、[`get_state`](@ref)関数を使用して引き続きアクセスできます。

# フィールド

  * `options`:         デバッグ情報によって拡張されるオプション
  * `debugDictionary`: 異なるアクションのデバッグを追跡するための`Dict{Symbol,DebugAction}`

# コンストラクタ

```
DebugSolverState(o,dA)
```

デバッグ装飾されたオプションを構築します。ここで、`dD`は次のようにすることができます。

  * [`DebugAction`](@ref)の場合、それは`：Iteration`で辞書内に格納されます。
  * [`DebugAction`](@ref)の配列。
  * `Dict{Symbol,DebugAction}`。
  * [`DebugFactory`](@ref)のためのシンボル、文字列、および整数の配列。
