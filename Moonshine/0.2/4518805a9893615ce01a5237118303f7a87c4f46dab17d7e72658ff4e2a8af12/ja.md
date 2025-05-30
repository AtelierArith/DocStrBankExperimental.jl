```julia
struct Sample <: AbstractVector{Moonshine.Sequence}
```

ハプロタイプのサンプルとそれに関する情報を含みます。

[反復インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration)と[配列インターフェース](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array)を実装しています。

# フィールド

  * `H::Vector{Moonshine.Sequence}`: ハプロタイプのベクター
  * `μ::Float64`: スケーリングされていない（ローカスごとの）突然変異率
  * `ρ::Float64`: スケーリングされていない（ローカスごとの）再結合率
  * `Ne::Float64`: 有効な個体群サイズ
  * `sequence_length::Float64`: 配列の長さ
  * `positions::Vector{Float64}`: マーカーの位置
  * `coefs::Tuple{Float64, Float64}`: 位置の直線の係数

# コンストラクタ

!!! info
    [msprime](https://tskit.dev/msprime/docs/stable/intro.html)を使用して[バイナリ突然変異モデル](https://tskit.dev/msprime/docs/stable/api.html#msprime.BinaryMutationModel)によりランダムコンストラクタでサンプルシーケンスを生成します。


```julia
Sample(H, μ, ρ, Ne, sequence_length, positions, coefs)
Sample(H, μ, ρ, Ne, sequence_length, positions, coefs)
```

[`packages/Moonshine/7JVTP/src/Sample.jl:33`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sample.jl)で定義されています。

```julia
Sample(H; μ, ρ, Ne, sequence_length, positions)
```

[`packages/Moonshine/7JVTP/src/Sample.jl:49`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sample.jl)で定義されています。

```julia
Sample(ts)
```

[`packages/Moonshine/7JVTP/src/Sample.jl:64`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sample.jl)で定義されています。

```julia
Sample(rng, n, μ, ρ, Ne, sequence_length)
```

[`packages/Moonshine/7JVTP/src/Sample.jl:102`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Sample.jl)で定義されています。

ここで：

  * `n`: シーケンスの数
  * `rng`: 擬似乱数生成器
  * `ts`: [ツリーシーケンス](https://tskit.dev/tskit/docs/latest/python-api.html#the-treesequence-class)
