フロー チャネルと多孔質媒体の間の界面での質量フラックス (kg/m^2-s) を計算する関数。圧力駆動フラックスは界面で無視されると仮定されます。

# 使用法

interface*flux!(jks::Array{T,1},C*ch, C*pm, dgm*obj::WorkSpace, molwts::Array{T}, Temp::T, δ::T)

  * jks : 種類フラックスのストレージ (1D 配列)
  * C_ch : フロー チャネル内の濃度
  * C_pm : 多孔質媒体内の濃度
  * dgm_obj : DGM フラックス計算のための拡散行列
  * molwts  : 分子量のベクトル
  * Temp : 温度 (K)
  * δ   : セル中心間の距離
