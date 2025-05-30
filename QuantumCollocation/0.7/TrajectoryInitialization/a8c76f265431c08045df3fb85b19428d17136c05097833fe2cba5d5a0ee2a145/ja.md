```
unitary_geodesic(U_init, U_goal, times; kwargs...)
```

指定された時刻でU*initとU*goalを接続する測地線を計算します。異なる時刻や[0,1]の範囲外の可能性を考慮します。

# 引数

  * `U_init::AbstractMatrix{<:Number}`: 初期ユニタリ演算子。
  * `U_goal::AbstractMatrix{<:Number}`: 目標ユニタリ演算子。
  * `times::AbstractVector{<:Number}`: 測地線を評価する時刻。

# キーワード引数

  * `return_unitary_isos::Bool=true`: trueの場合、各列がユニタリアイソベクである行列を返します。すなわち、vec(vcat(real(U), imag(U)))。falseの場合、ユニタリ行列のベクトルを返します。
  * `return_generator::Bool=false`: trueの場合、測地線を生成する有効ハミルトニアンを返します。
