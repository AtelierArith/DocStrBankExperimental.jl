```
PathResult
```

`PathResult`は、[`AbstractPathTracker`](@ref)（例：[`EndgameTracker`](@ref）を使用して[`track`](@ref)でパスを追跡した結果です。

## フィールド

一般的な解の情報：

  * `return_code`: 以下のリターンコードのリストを参照してください。
  * `solution::V`: 解ベクトル。
  * `t::Float64`: `solution`が計算されたときの`t`の値。`return_code`が`:at_infinity`の場合、これはその決定がなされたときの値です。
  * `accuracy::Float64`: 計算された解の（相対的）精度の推定値。
  * `residual::Float64`: `H(solution,t)`の無限ノルム。
  * `condition_jacobian::Float64`: 解におけるヤコビアンの条件数。高い条件数は、特異解または正の次元成分上の解を示します。
  * `singular::Bool`: 解が特異と見なされるかどうか。
  * `winding_number:Union{Nothing, Int}`: 計算された巻き数。この値は解の重複度の下限です。Cauchyエンドゲームが使用されなかった場合は$nothing$です。
  * `extended_precision::Bool`: `solution`の精度を達成するために拡張精度が必要かどうかを示します。
  * `path_number::Union{Nothing,Int}`: パスの番号（オプション）。
  * `start_solution::Union{Nothing,V}`: パスの開始解（オプション）。

性能情報：

  * `accepted_steps::Int`: パス追跡中に受け入れられたステップの数。
  * `rejected_steps::Int`: パス追跡中に拒否されたステップの数。
  * `extended_precision_used::Bool`: パスを追跡するために拡張精度が必要だったかどうかを示します。

追加のパスおよび解の情報

  * `valuation::Vector{Float64}`: $x(t)$のプイセウス級数展開の評価の近似。
  * `last_path_point::Tuple{V,Float64}`: 解が計算される前の最後のペア$(x,t)$。解がCauchyエンドゲームで計算された場合、ペア$(x,t)$はエンドゲームを再実行するために使用できます。

## リターンコード

可能なリターンコードは次のとおりです：

  * `:success`: `EndgameTracker`が解を得ました。
  * `:at_infinity`: `EndgameTracker`は、そのパスが無限に発散していると判断したため、パスの追跡を停止しました。
  * `:at_zero`: `EndgameTracker`は、そのパスに少なくとも1つの座標が0である解があると判断したため、パスの追跡を停止しました。これは、オプション`zero_is_at_infinity`が`true`の場合にのみ発生します。
  * `:excess_solution`: システムの解のために、システムを修正する必要があり、人工的な解が導入され、この解はその1つです。
  * 追跡の終了を示すさまざまなリターンコード
