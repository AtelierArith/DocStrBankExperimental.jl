バイナリ拡散係数とクヌーセン拡散係数を計算する関数で、DGMフラックスの評価に必要です。

# 使用法

effective*coefficients!(dgm*obj::WorkSpace, pm::Properties, sp_trd, p::Float64, T::Float64 ,molwts::Array{Float64})

  * dgm_obj : 拡散係数行列を格納するWorkSpace型の構造体
  * pm : 多孔質媒体の特性（Properties型の構造体）
  * sp*trd : TransportPropertiesのcreate*transport_dataを呼び出すことで得られる種の輸送データの配列
  * p : 圧力（Pa）
  * T : 温度（K）
  * molwts : 分子量ベクトル
