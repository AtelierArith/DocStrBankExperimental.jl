```
RecordSolverState <: AbstractManoptSolverState
```

任意の [`AbstractManoptSolverState`](@ref) に記録機能を持つデコレーターを追加します。内部的には、`Symbol` を参照として使用して、いくつかの同時モードのための [`RecordAction`](@ref) を保存する辞書が保持されます。デフォルトモードは `:Iteration` で、これは反復中に記録された情報を保存するために使用されます。RecordActions は `:Start` または `:Stop` に追加され、開始時または停止時点での値を記録します。

元のオプションには、[`get_state`](@ref) 関数を使用して引き続きアクセスできます。

# フィールド

  * `options`          デバッグ情報によって拡張されたオプション
  * `recordDictionary` すべての異なる記録された値を追跡するための `Dict{Symbol,RecordAction}`

# コンストラクタ

```
RecordSolverState(o,dR)
```

記録装飾された [`AbstractManoptSolverState`](@ref) を構築します。ここで、`dR` は次のいずれかです。

  * [`RecordAction`](@ref) の場合、それは `:Iteration` の辞書内に保存されます。
  * [`RecordAction`](@ref) の配列の場合、それは `recordDictionary`(@ref) として保存されます。
  * `Dict{Symbol,RecordAction}` の場合。
