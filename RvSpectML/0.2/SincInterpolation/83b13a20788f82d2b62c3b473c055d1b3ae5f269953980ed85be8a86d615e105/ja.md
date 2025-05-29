`interp_chunk_to_shifted_grid_sinc( chunk_of_spectrum, wavelengths, boost_factor )` は、sinc 補間を使用してポイントのグリッドに補間されたスペクトルを返します。

# 引数:

  * chunk*of*spectrum
  * wavelengths: chunk が補間される位置の AbstractRange または AbstractArray
  * boost*factor: wavelengths を boost*factor で割る

オプションの引数:

  * Filter: 事前に割り当てられたワークスペースを持つベクター (長さ >= 1 の場合)

# 戻り値

  * flux_out
