```
directsum(x::Ket, y::Ket)
```

二つの [`Ket`](@ref) の [`directsum`](@ref) を使ってスピノールを構築します。結果は `[x.data;y.data]` によって与えられるデータを持つ [`Ket`](@ref) であり、その基底は対応する [`SumBasis`](@ref) によって与えられます。**注意**: 結果の状態は正規化されていません！
