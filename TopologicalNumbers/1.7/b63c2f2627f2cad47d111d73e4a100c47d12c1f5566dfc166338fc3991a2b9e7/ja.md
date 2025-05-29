```
LBFProblem{T1<:Function,T2<:AbstractVector,T3<:Union{Tuple,AbstractVector,Int},T4<:Real,T5<:Bool} <: TopologicalNumbersProblems
```

$$
k
$$

-局所値のベリー流束を計算するための問題を表す構造体です。

# フィールド

  * `H::T1`: 系を定義するハミルトニアン関数 `H=H(k)`。`k` は波数ベクトルの `AbstractVector`（または `Tuple`）です。`k` の次元は2でなければなりません。
  * `n::T2`: ベリー流束を計算する際の波数を表す2つの `Int` 要素を含む `AbstractVector`（または `Tuple`）。`n` の次元は2でなければなりません。
  * `N::T3`: ブリルアンゾーンの1方向の点の数。デフォルトは51です。
  * `gapless::T4`: バンドをギャップレスと見なすための閾値。デフォルトは0.0です。
  * `rounds::T5`: 返される変数を丸めるかどうかを示すブール値。デフォルトはtrueです。

# 例

```julia
julia> 
```
