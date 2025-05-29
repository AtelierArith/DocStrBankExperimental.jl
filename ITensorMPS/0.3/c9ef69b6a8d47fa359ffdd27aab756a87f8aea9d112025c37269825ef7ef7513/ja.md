```
sim[!](siteinds, commoninds, M1::MPO, M2::MPS, args...; kwargs...)
sim[!](siteinds, commoninds, M1::MPO, M2::MPO, args...; kwargs...)
```

`M1` と `M2` に共通するサイトインデックスに sim を適用します。

新しい MPS/MPO を返します。MPS/MPO の ITensor は元の ITensor のストレージのビューになります。
