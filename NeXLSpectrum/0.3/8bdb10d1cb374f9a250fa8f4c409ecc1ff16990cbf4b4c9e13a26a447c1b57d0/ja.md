plane(hss::HyperSpectrum, chs::AbstractUnitRange{<:Integer}, normalize=false)

連続したデータチャネルの範囲を配列に合計します。結果の次元はHyperSpectrumの次元より1つ少なく、情報が失われないようにFloat64として保存されます。
