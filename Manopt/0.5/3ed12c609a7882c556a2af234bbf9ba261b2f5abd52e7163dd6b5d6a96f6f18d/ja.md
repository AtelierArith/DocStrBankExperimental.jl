```
CyclicProximalPointState <: AbstractManoptSolverState
```

は[`cyclic_proximal_point`](@ref)アルゴリズムのオプションを格納します。これらは

# フィールド

  * `p::P`: 現在の反復を格納する多様体$\mathcal M$上の点
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `λ`:         各反復（サイクル$k$）ごとの$λ_k$の値を計算する関数
  * `oder_type`: ランダムに順序を入れ替えたシーケンス（`:FixedRandomOrder`）、サイクルごとに入れ替えたシーケンス（`:RandomOrder`）、またはデフォルトの線形シーケンスのいずれかを使用するかどうか。

# コンストラクタ

```
CyclicProximalPointState(M::AbstractManifold; kwargs...)
```

オプションを生成します

## 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体$\mathcal M$

# キーワード引数

  * `evaluation_order=:LinearOrder`: `order_type`を指定
  * `λ=i -> 1.0 / i` $λ_k, k ∈ \mathcal N$を計算する関数
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体$\mathcal M$上の点
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`: 停止基準が満たされていることを示すファンクタ

# 参照

[`cyclic_proximal_point`](@ref)
