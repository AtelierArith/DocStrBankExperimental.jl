```
DiscreteExplicitMDP(S,A,T,R,γ,[p₀],[terminals=Set()])
```

タプル (S,A,T,R,γ) によって定義された MDP を作成します。

# 引数

## 必須

  * `S`,`A`: 状態および行動空間（通常は `Vector`）
  * `T::Function`: 遷移確率分布関数; $T(s,a,s')$ は、行動 $a$ を取った後に状態 $s$ から状態 $s'$ に遷移する確率です。
  * `R::Function`: 報酬関数; $R(s,a)$ は、状態 $s$ で行動 $a$ を取ったときの報酬です。
  * `γ::Float64`: 割引率。

## オプション

  * `p₀=Uniform(S)`: 初期状態分布（他のオプションについては `POMDPModelTools.Deterministic` および `POMDPModelTools.SparseCat` を参照してください）。

## キーワード

  * `terminals=Set()`: 終端状態のセット。一度終端状態に達すると、これ以上の行動を取ったり報酬を受け取ったりすることはできません。
