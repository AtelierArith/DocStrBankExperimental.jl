```
HMM([a, ]A, B) -> HMM
```

遷移行列 `A` と観測分布 `B` を持つHMMを構築します。初期状態分布 `a` が指定されていない場合、均一分布が仮定されます。

観測分布は異なるタイプ（例えば `Normal` と `Exponential`）であっても構いませんが、同じ次元でなければなりません。

また、`B` は発生行列であり、`B[i,j]` は状態 `i` でシンボル `j` を観測する確率です。

**引数**

  * `a::AbstractVector{T}`: 初期確率ベクトル。
  * `A::AbstractMatrix{T}`: 遷移行列。
  * `B::AbstractVector{<:Distribution{F}}`: 観測分布。
  * または `B::AbstractMatrix`: 発生行列。

**例**

```julia
using Distributions, HMMBase
# 分布から
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
# 発生行列から
hmm = HMM([0.9 0.1; 0.1 0.9], [0. 0.5 0.5; 0.25 0.25 0.5])
```
