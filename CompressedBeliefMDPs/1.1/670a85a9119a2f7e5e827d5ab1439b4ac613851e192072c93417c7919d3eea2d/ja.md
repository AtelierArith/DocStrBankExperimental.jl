```
make_numerical(B, pomdp)
```

信念のセット `B` を数値アルゴリズム/圧縮器による処理に適した数値行列表現に変換するヘルパー関数です。

# 引数

  * `B::Vector{<:Any}`: 信念のベクトル。
  * `pomdp::POMDP`: 信念に関連するPOMDPモデル。

# 戻り値

  * `Matrix{Float64}`: 各行が `B` の信念の数値表現に対応する行列。

# 使用例

```julia
B = [belief1, belief2, belief3]
B_numerical = make_numerical(B, pomdp)
```
