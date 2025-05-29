```
Wmerge, Hmerge, mergeseq = colmerge2to1pq(W::AbstractArray, H::AbstractArray, n::Integer)
```

`W`と`H`のコンポーネントをマージします（`W`の列と`H`の行）まで、`n`個のコンポーネントのみが残ります。

`Wmerge`と`Hmerge`は、`n`個のコンポーネントを持つマージ結果です。

`mergeseq`はマージペアIDのシーケンス（id1, id2）です。`W`の列数より大きい値は、前のマージステップの出力を示します。
