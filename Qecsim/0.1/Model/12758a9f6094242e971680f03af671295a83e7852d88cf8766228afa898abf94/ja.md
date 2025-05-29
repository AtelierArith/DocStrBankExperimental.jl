```
nkd(code) -> Tuple{Int,Int,Union{Int,Missing}}
```

物理キュービットの数を `n`、論理キュービットの数を `k`、コードの距離を `d`（不明な場合は `missing`）とする形式で `(n, k, d)` を返します。

!!! note "抽象メソッド"
    このメソッドは、具体的なサブタイプまたは [`StabilizerCode`](@ref) のダックタイピング実装のために実装されるべきです。

