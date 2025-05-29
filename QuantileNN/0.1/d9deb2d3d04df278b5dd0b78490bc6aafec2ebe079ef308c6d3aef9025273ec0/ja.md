predict_smooth(qr::QNN, z::AbstractVector, bw::AbstractVector)

フィッティングされたモデルqrの点zでの分位数を予測します。ベクトルbwはバンド幅を含み、zと同じ長さ（各変数のバンド幅）であるか、長さ1のベクトル（すべての変数に同じバンド幅）であることができます。
