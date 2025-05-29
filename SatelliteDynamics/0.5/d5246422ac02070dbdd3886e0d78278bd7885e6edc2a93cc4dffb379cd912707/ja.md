GCRSからCIRS中間参照フレームへの変換を行うバイアス-歳差- nutation行列を計算します。この変換は、慣性空間に対する天体中間起源（CIO）のバイアス、歳差、およびnutationを修正します。

引数:

  * `epc::Epoch`: 変換のエポック

戻り値:

  * `rc2i::Matrix{<:Real}`: GCRS -> CIRSを変換する3x3回転行列
