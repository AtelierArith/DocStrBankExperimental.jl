二つのセル間の界面での質量フラックス（kg/m^2-s）をDGMを使用して計算する関数。この関数では境界セルでのフラックスは評価されません。n個のセルがある場合、n-1の内部セル面があります。

# 使用法

flux*dgm!(jks::Array{Array{T,1},1}, C::Array{Array{T,1},1}, pm::Properties, dgm*obj::WorkSpace , molwts::Array{T}, Temp::T, δ::T)

  * jks : フラックスを格納するためのベクトル{ベクトル}。jks[n]はn番目と(n+1)番目のセル間の界面でのフラックスを表します。
  * C : すべてのセルの濃度を含むベクトル{ベクトル}
  * pm : 多孔質媒体の特性（Properties型の構造体）
  * dgm_obj : 拡散係数行列を格納するWorkSpace型の構造体
  * sp*tr*data : TransportPropertiesのcreate*transport*dataを呼び出すことで得られる種輸送データの配列
  * molwts : 分子量のベクトル
  * Temp : 温度（K）
  * δ : セル中心間の距離
