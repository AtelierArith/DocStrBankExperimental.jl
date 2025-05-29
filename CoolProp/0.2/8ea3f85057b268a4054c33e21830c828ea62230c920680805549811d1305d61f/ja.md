```
AbstractState_update_and_1_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, output::Clong, out::Array{Float64})
AbstractState_update_and_1_out(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, output::AbstractString, out::Array{Float64})
```

AbstractStateの状態を更新し、ポインタを入力および出力として使用して配列計算を可能にすることで、AbstractStateから1つの出力値（温度、圧力、モル密度、モルエンタルピー、モルエントロピー）を取得します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `input_pair::Clong`: get*input*pair_indexから取得した入力ペアの整数値
  * `input_pair::AbstractString`:
  * `value1`: 最初の入力パラメータの配列へのポインタ
  * `value2`: 2番目の入力パラメータの配列へのポインタ
  * `length`: 配列に格納されている要素の数（入力と出力の両方は同じ長さでなければなりません）
  * `output`: 希望する出力のインデックス
  * `out`: 出力用の配列
