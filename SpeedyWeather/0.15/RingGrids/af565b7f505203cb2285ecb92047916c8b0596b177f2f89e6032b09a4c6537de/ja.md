`FullHEALPixArray`は、各リングにHEALPix緯度を使用する`AbstractFullGridArray`のフルグリッドの配列です。このタイプは、出力のために（縮小された）HEALPixGridからフルグリッドにデータを補間するために主に使用されます。

基盤となる`N`次元`data`の最初の次元は、リング順（0から360˚E、次に北から南）での水平次元を表し、他の次元は垂直および/または時間または他の次元に使用されます。水平グリッドの解像度パラメータは`nlat_half`（1つの半球の緯度リングの数、赤道を含む）であり、リングインデックスは`rings`に事前計算されています。フィールドは次のとおりです。

  * `data::AbstractArray`
  * `nlat_half::Int64`
  * `rings::Vector{UnitRange{Int64}}`
