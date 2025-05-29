```
tensorproduct!(C, A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, β=0, [backend, allocator])
```

2つのテンソル `A` と `B` のテンソル積（外積）を計算します。すなわち、インデックスが収束されていない [`tensorcontract!`](@ref) のラッパーです。このメソッドは、インデックスが実際にテンソル積を指定しているのか、真の収束を指定しているのかを確認します。オプションで、使用するバックエンド実装と、一時的なテンソルオブジェクトが必要な場合に使用されるアロケータを指定できます。

!!! warning
    オブジェクト `C` は `A` または `B` とエイリアスされてはいけません。


[`tensorproduct`](@ref) と [`tensorcontract!`](@ref) も参照してください。
