二つのセル間の質量フラックス (kg/m^2-s) を修正されたフィックモデルを使用して計算する関数。境界セルでのフラックスはこの関数では評価されません。n セルがある場合、n-1 の内部セル面があります。

# 使用法

flux*porous*media*fick!(jks::Array{Array{T,1},1}, C::Array{Array{T,1},1}, pm::Properties, sp*tr_data, ws::WorkSpace , molwts::Array{T}, Temp::T, δ::T)

  * jks : フラックスを格納するためのベクトル{ベクトル} jks[n] は n と (n+1) 番目のセル間のフラックスを表します
  * C : すべてのセルの濃度を含むベクトル{ベクトル}
  * pm : 多孔質媒体の特性 (Properties 型の構造体)
  * sp*tr*data : TransportProperties の create*transport*data を呼び出すことで得られる種輸送データの配列
  * ws : 拡散係数行列を格納する WorkSpace 型の構造体
  * molwts : 分子量のベクトル
  * Temp : 温度 (K)
  * δ : セル中心間の距離
