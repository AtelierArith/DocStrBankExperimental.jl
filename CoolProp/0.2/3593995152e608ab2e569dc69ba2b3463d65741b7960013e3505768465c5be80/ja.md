```
AbstractState_update_and_5_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, outputs::Array{Clong}, out1::Array{Float64}, out2::Array{Float64}, out3::Array{Float64}, out4::Array{Float64}, out5::Array{Float64})
AbstractState_update_and_5_out{S<:AbstractString}(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, outputs::Array{S}, out1::Array{Float64}, out2::Array{Float64}, out3::Array{Float64}, out4::Array{Float64}, out5::Array{Float64})
```

AbstractStateの状態を更新し、ポインタを入力として使用して、配列計算を可能にするためにAbstractStateから5つの共通出力（温度、圧力、モル密度、モルエンタルピー、モルエントロピー）を取得します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `input_pair::Clong`: get*input*pair_indexから取得した入力ペアの整数値
  * `input_pair::AbstractString`:
  * `value1`: 最初の入力パラメータの配列へのポインタ
  * `value2`: 2番目の入力パラメータの配列へのポインタ
  * `length`: 配列に格納されている要素の数（入力と出力の両方は同じ長さでなければなりません）
  * `outputs`: 希望する出力のインデックスの5要素ベクター
  * `out1`: 最初の出力用の配列
  * `out2`: 2番目の出力用の配列
  * `out3`: 3番目の出力用の配列
  * `out4`: 4番目の出力用の配列
  * `out5`: 5番目の出力用の配列
