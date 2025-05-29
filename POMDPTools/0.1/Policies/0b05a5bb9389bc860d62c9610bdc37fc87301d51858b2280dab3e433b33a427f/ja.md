```
AlphaVectorPolicy(pomdp::POMDP, alphas, action_map)
```

アルファベクトルからポリシーを構築します。

# 引数

  * `alphas`: |S| x (アルファベクトルの数) の行列またはアルファベクトルのベクトル。
  * `action_map`: 各アルファベクトルに対応するアクションのベクトル

    AlphaVectorPolicy{P<:POMDP, A}

アルファベクトルのセットを持つポリシーを表します。

`action`を使用して信念に対する最良のアクションを取得し、`alphavectors`および`alphapairs`を使用します。

# フィールド

  * `pomdp::P` POMDP問題
  * `n_states::Int` POMDP内の状態の数
  * `alphas::Vector{Vector{Float64}}` アルファベクトルのリスト
  * `action_map::Vector{A}` アルファベクトルに対応するアクションのリスト
