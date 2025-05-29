```
SCProblem{T1<:Function,T2<:Union{Int,Nothing},T3<:Union{Tuple,AbstractVector,Int},T4<:Bool} <: TopologicalNumbersProblems
```

第二チェルン数を計算するための問題を表す構造体です。

# フィールド

  * `H::T1`: 系を定義するハミルトニアン関数 `H=H(k, p)`。`k` は波数ベクトルの抽象ベクトル（またはタプル）で、`p` はパラメータを含みます。`k` の次元は4でなければなりません。
  * `Nfill::T2`: 満たされたバンドの数。`nothing` は半充填を意味します。デフォルトは `nothing` です。
  * `N::T3`: ブリルアンゾーン内の点の数。`Int` 型は均一メッシュを意味します。タプルまたはベクトルを指定することでメッシュを指定することもできます。デフォルトは30です。
  * `RV::T4`: `real` 値を返すかどうかを示すブール値。デフォルトはtrueです。

# 例

```julia
julia> 
```
