`interp_chunk_to_grid_sinc!( flux_out, var_out, chunk_of_spectrum, wavelengths )` グリッドポイントに対してsinc補間を使用して補間されたスペクトルを返します。

# 引数:

  * flux_out: (この配列に結果が格納されます)
  * var_out: (この配列に結果が格納されます)
  * chunk*of*spectrum
  * wavelengths: chunkが補間される位置のAbstractRangeまたはAbstractArray

オプション引数:

  * Filter: 事前に割り当てられたワークスペースを持つベクター（長さ>=1の場合）

# 戻り値

  * flux_out
