```
FCProblem{T1<:Function,T2<:Union{Tuple,AbstractVector,Int},T3<:Real,T4<:Bool} <: TopologicalNumbersProblems
```

最初のチェルン数を計算するための問題を表す構造体です。

# フィールド

  * `H::T1`: システムを定義するハミルトニアン関数 `H=H(k, p)`。`k` は波数ベクトルの抽象ベクトル（またはタプル）で、`p` はパラメータを含みます。`k` の次元は2でなければなりません。
  * `N::T2`: ブリルアンゾーンの1方向のポイント数。デフォルトは51です。
  * `gapless::T3`: バンドをギャップレスと見なすための閾値。デフォルトは0.0です。
  * `rounds::T4`: 返される変数を丸めるかどうかを示すブール値。デフォルトはtrueです。

# 例

```julia
julia> 
```
