```
CyclicProximalPointState <: AbstractManoptSolverState
```

は[`cyclic_proximal_point`](@ref)アルゴリズムのオプションを格納します。これらは

# フィールド

  * `p`:                  現在の反復値
  * `stopping_criterion`:  [`StoppingCriterion`](@ref)
  * `λ`:                  (@(i) -> 1/i) 各反復（サイクル$i$）ごとの$λ_k$の値のための関数
  * `oder_type`:          (`:LinearOrder`) ランダムに順序を入れ替えたシーケンス（`:FixedRandomOrder`）、サイクルごとに順序を入れ替えたシーケンス（`:RandomOrder`）、またはデフォルトの線形順序を使用するかどうか。

# コンストラクタ

```
CyclicProximalPointState(M, p)
```

次のキーワード引数を使用してオプションを生成します

  * `stopping_criterion`: (`StopAfterIteration(2000)`) [`StoppingCriterion`](@ref)。
  * `λ`:                  ( `i -> 1.0 / i`) $λ_k, k ∈ \mathbb N$を計算するための関数、
  * `evaluation_order`:   (`:LinearOrder`) 近接マップが適用される順序を示すシンボル。

# 参照

[`cyclic_proximal_point`](@ref) ```
