```
DiscreteExplicitPOMDP(S,A,O,T,Z,R,γ,[b₀],[terminals=Set()])
```

タプル (S,A,O,T,Z,R,γ) によって定義された POMDP を作成します。

# 引数

## 必須

  * `S`,`A`,`O`: 状態、行動、および観測空間（通常は `Vector`）
  * `T::Function`: 遷移確率分布関数; $T(s,a,s')$ は、行動 $a$ を取った後に状態 $s$ から状態 $s'$ に遷移する確率です。
  * `Z::Function`: 観測確率分布関数; $O(a, s', o)$ は、行動 $a$ の後に状態 $s'$ に到達したときに観測 $o$ を受け取る確率です。
  * `R::Function`: 報酬関数; $R(s,a)$ は、状態 $s$ で行動 $a$ を取ったときの報酬です。
  * `γ::Float64`: 割引率。

## オプション

  * `b₀=Uniform(S)`: 初期の信念/状態分布（他のオプションについては `POMDPModelTools.Deterministic` および `POMDPModelTools.SparseCat` を参照してください）。

## キーワード

  * `terminals=Set()`: 終端状態のセット。一度終端状態に到達すると、これ以上の行動を取ったり報酬を受け取ったりすることはできません。
