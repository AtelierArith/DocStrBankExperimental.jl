```
Block{T}()
Block(times::AbstractVector{DateTime}, values::AbstractVector{T})
Block(unchecked, times, values)
```

時系列データを表現します。

概念的には、これは `(time, value)` ペア、または「ノット」のリストです。時間は厳密に増加している必要があります — すなわち、重複したタイムスタンプは許可されていません。

コンストラクタ `Block(times, values)` は、入力データがこの制約を満たしていることを確認しますが、`Block(unchecked, times, values)` はチェックをスキップします。これは主に内部使用を目的としており、呼び出し元が `times` と `values` の有効性に対する責任を負います。

!!! danger
    `TimeDag` は `Block` のインスタンスを完全に不変であると見なします。したがって、ブロックを受け入れる関数（例: [`TimeDag.run_node!`](@ref)）を使用する際には、`times` または `values` メンバーを変更してはいけません。

