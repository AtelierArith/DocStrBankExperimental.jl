```
Partition(; x = 1, y = 1, z = 1)
```

`x`（第一）、`y`（第二）、`z`（第三）次元の領域の分割を表す`Partition`を返します。

# キーワード引数:

  * `x`: 第一次元の分割
  * `y`: 第二次元の分割
  * `z`: 第三次元の分割

位置引数として指定された場合、`x`は最初の引数、`y`は第二の引数、`z`は第三の引数になります。

`x`、`y`、`z`は次のように指定できます：

  * `x::Int`: 第一次元に`x`個のプロセッサを割り当てる
  * `Equal()`: 残りのプロセス間で`x`を均等に分割する（複数の方向には対応していません）
  * `Fractional(ϵ₁, ϵ₂, ..., ϵₙ):` `N`個のプロセス間で不均等に領域を分割します。総作業は`W = sum(ϵᵢ)`であり、各プロセスには`ϵᵢ / W`の領域が割り当てられます。
  * `Sizes(n₁, n₂, ..., nₙ)`: 領域を不均等に分割します。総作業は`W = sum(nᵢ)`であり、各プロセスには`nᵢ`が割り当てられます。

# 例:

```jldoctest
julia> using Oceananigans; using Oceananigans.DistributedComputations

julia> Partition(1, 4)
Partition across 4 = 1×4×1 ranks:
└── y: 4

julia> Partition(x = Fractional(1, 2, 3, 4))
Partition across 4 = 4×1×1 ranks:
└── x: Fractional(0.1, 0.2, 0.3, 0.4)

```
