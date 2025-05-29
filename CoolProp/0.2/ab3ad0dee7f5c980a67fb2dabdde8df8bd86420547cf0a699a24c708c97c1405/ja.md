```
AbstractState_update_and_common_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, hmolar::Array{Float64}, smolar::Array{Float64})
AbstractState_update_and_common_out(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, hmolar::Array{Float64}, smolar::Array{Float64})

AbstractStateの状態を更新し、ポインタを入力および出力として使用して、AbstractStateから5つの共通出力（温度、圧力、モル密度、モルエンタルピー、モルエントロピー）を取得します。配列計算を可能にします。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `input_pair::Clong`: get*input*pair_indexから取得した入力ペアの整数値
  * `input_pair::AbstractString`:
  * `value1`: 最初の入力パラメータの配列へのポインタ
  * `value2`: 2番目の入力パラメータの配列へのポインタ
  * `length`: 配列に格納されている要素の数（入力と出力の両方が同じ長さでなければなりません）
  * `T`: 温度の配列へのポインタ
  * `p`: 圧力の配列へのポインタ
  * `rhomolar`: モル密度の配列
  * `hmolar`: モルエンタルピーの配列
  * `smolar`: モルエントロピーの配列

# 例

```

julia julia> handle = AbstractState*factory("HEOS", "Water&Ethanol"); julia> pq*inputs = get*input*pair*index("PQ*INPUTS"); julia> AbstractState*set*fractions(handle, [0.4, 0.6]); julia> T = [0.0]; p = [0.0]; rhomolar = [0.0]; hmolar = [0.0]; smolar = [0.0]; julia> AbstractState*update*and*common*out(handle, pq*inputs, [101325.0], [0.0], 1, T, p, rhomolar, hmolar, smolar); julia> AbstractState*free(handle); ```
