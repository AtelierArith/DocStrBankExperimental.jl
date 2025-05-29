```
tensorcontract([IC], A, IA, [conjA], B, IB, [conjB], [α=1]; [backend=..., allocator=...])
tensorcontract(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, pAB::Index2Tuple, α=1, [backend, allocator]) # expert mode
```

テンソル `A` のインデックスを、イテラブル `IA` と `IB` で同じラベルを割り当てることによって、テンソル `B` の対応するインデックスと契約します。結果のテンソルのインデックスは、`IA` または `IB` のいずれかにのみ現れるインデックスに対応し、オプションの引数 `IC` を指定することで順序を付けることができます。デフォルトでは、`A` のすべてのオープンインデックスの後に `B` のすべてのオープンインデックスが続きます。配列の内部契約は、すべてのラベルが `IA` または `IB` に別々に一度だけ現れ、オープンインデックスの場合は一度、契約インデックスの場合は二度、`IA` と `IB` の和集合に現れるようにするために、最初に `tensortrace` で処理する必要があることに注意してください。

オプションで、記号 `conjA` と `conjB` を使用して、入力テンソルを共役させることができます。

詳細は [`tensorcontract!`](@ref) を参照してください。
