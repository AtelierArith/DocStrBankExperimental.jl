`interp_chunk_to_shifted_grid_sinc!( flux_out, var_out, chunk_of_spectrum, wavelengths, boost_factor )` サンプルを sinc 補間を使用してポイントのグリッドに補間します。

# 引数:

  * flux_out: (この配列に結果が格納されます)
  * var_out: (この配列に結果が格納されます)
  * chunk*of*spectrum
  * wavelengths: chunk が補間される場所の AbstractRange または AbstractArray
  * boost*factor: wavelengths を boost*factor で割ります

オプションの引数:

  * Filter: 事前に割り当てられたワークスペースを持つベクター (長さ >= 1 の場合)

# 戻り値

  * flux_out
