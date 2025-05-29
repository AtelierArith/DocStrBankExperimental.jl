```
Wmerge, Hmerge, WHstage, Err = mergecolumns(W, H, mergeseq; tracemerge=false)
```

`W` と `H` のコンポーネントを、マージペアIDのシーケンス `mergeseq` に従ってマージします（`W` の列と `H` の行）。

`Wmerge` と `Hmerge` はマージされた結果です。

`WHstage::Vector{Tuple{Matrix, Matrix}}` には各マージステージの結果が含まれています。`tracemerge=false` の場合、`WHstage` は空です。

`Err::Vector` には各マージステージのマージペナルティが含まれています。
