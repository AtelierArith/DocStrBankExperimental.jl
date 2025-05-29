```
tensoradd([IC=IA], A, IA, [conjA], B, IB, [conjB], [α=1, [β=1]]; [backend=..., allocator=...])
tensoradd(A, pA::Index2Tuple, conjA, B, pB::Index2Tuple, conjB, α=1, β=1, [backend, allocator]) # expert mode
```

配列 `A` と `B` を加算する結果を返します。ここで、イテラブル `IA` と `IB` は、加算するために配列データがどのように置換されるべきかを示します。より具体的には、このメソッドの結果は `α * permutedims(A, pA) + β * permutedims(B, pB)` に相当し、ここで `pA`（`pB`）は `IC = IA[pA]`（`IB[pB]`）となるような置換です。しかし、`tensoradd` の実装は平均してより効率的であり、一時的な置換配列は作成されません。

オプションとして、記号 `conjA` と `conjB` を使用して、入力テンソルを共役にするか（`true`）、しないか（`false`）を指定できます。

詳細は [`tensoradd!`](@ref) を参照してください。
