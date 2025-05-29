resample_elwise(uvals::Vector{AbstractUncertainValue}, n::Int) 

`uvals`の各要素を`n`回再サンプリングします。返されるベクトルのi番目のエントリは、`uvals[i]`の`n`個のユニークなドローからなる`n`要素のベクトルです。
