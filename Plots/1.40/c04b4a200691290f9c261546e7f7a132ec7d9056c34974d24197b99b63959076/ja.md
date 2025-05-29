```
density(x)
density!(x)
```

xのカーネル密度推定の線グラフを作成します。密度プロットの滑らかさは`bandwidth`（実数の正の数）によって定義されます。

# 引数

  * `x`: 確率密度推定のためのサンプルのAbstractVector

# キーワード引数

  * `trim`::Bool: 分布の尾を切り取ることを有効にします。
  * `bandwidth`::Number: 低いバンド幅はアンダースムージングを引き起こし、高いバンド幅はオーバースムージングを引き起こします。

# 例

```julia-repl
julia> density(randn(100), bandwidth = -0.01, trim = false)
output : ERROR: Bandwidth must be positive

julia> density(randn(100), bandwidth = 0.1, trim = false)  # 極端さとアンダースムージングを持つ曲線
julia> density(randn(100), bandwidth = 10, trim = true)  # 極端さのないオーバースムージングの曲線
```

# 例

```julia-repl
julia> using StatsPlots
julia> density(randn(100_000))
```
