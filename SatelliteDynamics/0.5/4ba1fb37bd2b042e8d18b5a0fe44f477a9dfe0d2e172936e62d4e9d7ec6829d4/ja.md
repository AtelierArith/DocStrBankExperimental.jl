地球の向きデータオブジェクト。このオブジェクトは、地球の向きパラメータ（EOP）と天体中間極（CIP）オフセットを格納します。このオブジェクトは、特定の修正ユリウス日（MJD）に対する地球の向きパラメータを計算するために使用されます。

属性：

  * `data::Dict{Int, Tuple{Float64, Float64, Float64}}` EOPデータは、MJDをキーとし、(UT1-UTC [s], xp [rad], yp [rad])のタプルを値とする辞書として格納されています。
  * `last_eop_data::Int` EOPデータの最後のMJD値。
  * `dXdYData::Dict{Int, Tuple{Float64, Float64}}` CIPオフセットは、MJDをキーとし、(dX [rad], dY [rad])のタプルを値とする辞書として格納されています。
  * `last_dxdy_mjd::Int` dX/dYデータの最後のMJD値。
