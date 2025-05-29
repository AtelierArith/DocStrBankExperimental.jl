nfft(k, f, rest...; kwargs...)

配列 `f` の nfft を行列 `k` に含まれるノードに対して計算します。出力は長さ M=`size(nodes,2)` のベクトルです。
