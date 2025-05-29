```
localpart(dv) -> AbstractDVec
```

このMPIランクにある`dv`の部分を取得します。MPIで分散できないベクトル（[`DVec`](@ref Main.DictVectors.DVec)sおよび[`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec)s）の場合は、`dv`自体を返します。
