```
Z2Problem{T1<:Function,T2<:Union{Int,Nothing},T3<:Union{Tuple,AbstractVector,Int},T4<:Bool} <: TopologicalNumbersProblems
```

Z2数を計算するための問題を表す構造体です。

# フィールド

  * `H::T1`: 系を定義するハミルトニアン関数 `H=H(k, p)`。`k` は波数ベクトルの抽象ベクトル（またはタプル）で、`p` はパラメータを含みます。`k` の次元は2でなければなりません。
  * `Nfill::T2`: 満たされたバンドの数。`nothing` は半充填を意味します。デフォルトは `nothing` です。
  * `N::T3`: ブリルアンゾーンの1方向のポイント数。デフォルトは50です。
  * `rounds::T4`: 返される変数を丸めるかどうかを示すブール値。デフォルトはtrueです。
  * `TR::T4`: ブリルアンゾーンの残りの部分を計算するかどうかを示すブール値。`true` の場合、`solve` は追加の結果 `TRTopologicalNumber` を返します。計算が通常通り行われた場合、`TRTopologicalNumber` は `TopologicalNumber` と等しくなります。デフォルトはfalseです。

# 例

```julia
julia> 
```
