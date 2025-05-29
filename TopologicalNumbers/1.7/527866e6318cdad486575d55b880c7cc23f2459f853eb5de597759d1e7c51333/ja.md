```
struct BPProblem{T1<:Function,T2<:Union{Tuple,AbstractVector,Int},T3<:Real,T4<:Bool} <: TopologicalNumbersProblems
```

`BPProblem`構造体は、ベリー位相を計算するための問題を表します。

# フィールド

  * `H::T1`: システムを定義するハミルトニアン関数 `H=H(k, p)`。`k`は波数ベクトルの抽象ベクトル（またはタプル）で、`p`はパラメータを含みます。`k`の次元は1でなければなりません。
  * `N::T2`: ブリルアンゾーンの1方向のポイント数。デフォルトは51です。
  * `gapless::T3`: バンドをギャップレスと見なすための閾値。デフォルトは0.0です。
  * `rounds::T4`: 戻り値を丸めるかどうかを示すブール値。デフォルトはtrueです。

# 例

```julia
julia> 
```
