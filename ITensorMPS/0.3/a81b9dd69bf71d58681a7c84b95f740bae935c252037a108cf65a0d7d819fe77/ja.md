```
noprime[!](siteinds, commoninds, M1::MPO, M2::MPS, args...; kwargs...)
noprime[!](siteinds, commoninds, M1::MPO, M2::MPO, args...; kwargs...)
```

`M1` と `M2` に共有されるサイトインデックスに noprime を適用します。

新しい MPS/MPO を返します。MPS/MPO の ITensor は、元の ITensor のストレージのビューになります。
