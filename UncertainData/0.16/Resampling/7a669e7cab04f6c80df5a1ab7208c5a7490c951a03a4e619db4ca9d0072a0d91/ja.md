resample(uvals::Vector{AbstractUncertainValue}, n::Int) 

`uvals`をデータセットとして扱い、`n`回再サンプリングします。 `uvals`の`n`個の再サンプリングされたドローを返し、それぞれが`length(uvals)`要素のベクトルです。返される各ベクトルのi番目の要素は、`uvals[i]`のユニークなドローです。
