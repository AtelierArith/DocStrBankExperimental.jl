```
tensorcontract!(C, A, pA, conjA, B, pB, conjB, pAB, α=1, β=0 [, backend, allocator])
```

`C = β * C + α * permutedims(contract(opA(A), opB(B)), pAB)` を中間のテンポラリを作成せずに計算します。ここで、`A` と `B` は、`A` のインデックス `pA[2]` が `B` のインデックス `pB[1]` と契約されるように契約されます。残りのインデックス `(pA[1]..., pB[2]...)` は、`pAB` に従って順序が変更されます。操作 `opA` は、`conjA` が `false` の場合は `identity` として、`conjA` が `true` の場合は `conj` として機能します; 操作 `opB` は同様に `conjB` によって決定されます。オプションで、使用するバックエンド実装と、一時的なテンソルオブジェクトが必要な場合に使用されるアロケータを指定できます。

!!! warning
    オブジェクト `C` は `A` または `B` とエイリアスされてはいけません。


詳細は [`tensorcontract`](@ref) を参照してください。
