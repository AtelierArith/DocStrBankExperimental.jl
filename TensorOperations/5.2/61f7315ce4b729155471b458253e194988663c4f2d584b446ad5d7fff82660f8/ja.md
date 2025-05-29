```
tensorproduct([IC], A, IA, [conjA], B, IB, [conjB], [α=1]; [backend=..., allocator=...])
tensorproduct(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, [backend, allocator]) # expert mode
```

2つのテンソル `A` と `B` のテンソル積（外積）を計算します。すなわち、`ndims(C) = ndims(A) + ndims(B)` となる新しいテンソル `C` を返します。出力テンソルのインデックスは、指定されたインデックスによって入力テンソルのインデックスに関連しています。基本的には、インデックスが収束されない [`tensorcontract`](@ref) の特別なケースです。このメソッドは、インデックスが本当にテンソル積を指定しているか、真の収束を指定しているかを確認します。

オプションとして、記号 `conjA` と `conjB` を使用して、入力テンソルを共役させることができます。

さらに [`tensorproduct!`](@ref) および [`tensorcontract`](@ref) も参照してください。
