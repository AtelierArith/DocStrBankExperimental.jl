```
tensorcopy!(C, A, pA::Index2Tuple, conjA=false, α=1, [backend, allocator])
```

テンソル `A` の内容を `C` にコピーします。ここで、`A` の次元は置換と再分配 `pA` に従って置換されます。

このメソッドの結果は `α * permutedims!(C, A, pA)` と同等です。

オプションとして、フラグ `conjA` を使用して、入力テンソルを共役にするかどうか（`true`）を指定できます。

!!! warning
    オブジェクト `C` は `A` とエイリアスされてはいけません。


関連情報として [`tensorcopy`](@ref) と [`tensoradd!`](@ref) を参照してください。
