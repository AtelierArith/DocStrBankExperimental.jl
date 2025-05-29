```
WNProblem{T1<:Function,T2<:AbstractVector,T3<:Int,T4<:Real,T5<:Bool} <: TopologicalNumbersProblems
```

ウエイリノードを計算するための問題を表す構造体です。

# フィールド

  * `H::T1`: システムを定義するハミルトニアン関数 `H=H(k)`。`k` は波数ベクトルの抽象ベクトル（またはタプル）です。`k` の次元は3でなければなりません。
  * `n::T2`: 波数を表す2つの `Int` 要素を含む `AbstractVector`（または `Tuple`）。波数は ($2\pi n/N$) です。`n` の次元は3でなければなりません。
  * `N::T3`: ブリルアンゾーンの1方向の点の数。デフォルトは51です。
  * `gapless::T4`: バンドをギャップレスと見なすための閾値。デフォルトは0.0です。
  * `rounds::T5`: 返される変数を丸めるかどうかを示すブール値。デフォルトはtrueです。

# 例

```julia
julia> 
```
