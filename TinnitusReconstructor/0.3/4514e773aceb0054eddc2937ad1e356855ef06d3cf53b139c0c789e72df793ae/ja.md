```
binnedrepr2spect(s::BinnedStimgen, binned_repr::AbstractArray{T}) where {BS<:BinnedStimgen,T}
```

バイナリ表現をスペクトル表現に変換します。ビンの数は `n_bins` パラメータで指定できます。デフォルトでは `s.n_bins` が使用されます。

`n_frequencies x n_trials` のスペクトル配列を返します。ここで、`n_trials` = size(binned_repr, 2) です。
