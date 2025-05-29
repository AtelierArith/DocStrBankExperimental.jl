Ficksの法則を使用してKg/m^2-sで拡散フラックスを計算する関数。フラックスは合計がゼロになるように修正されています。

# 使用法

flux_ficks!(jks::Array{T}, Dkm::Array{T} ,C1::Array{T}, C2::Array{T}, δ::T)

  * jks : フラックスのベクトル
  * C1 : 濃度ベクトル
  * C2 : 濃度ベクトル
  * δ  : セル中心間の距離
