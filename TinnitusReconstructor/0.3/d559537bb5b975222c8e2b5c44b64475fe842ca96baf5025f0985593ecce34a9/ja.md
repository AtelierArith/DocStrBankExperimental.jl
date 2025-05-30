```
spect2binnedrepr(s::BinnedStimgen, spect::AbstractVecOrMat{T}; n_bins::I = 0) where {BS<:BinnedStimgen,T,I<:Integer}
```

スペクトル表現をビン化された表現に変換します。ビンの数は `n_bins` パラメータで指定できます。デフォルトでは `s.n_bins` が使用されます。

各周波数ビンにおけるスペクトルの振幅を含む `n_trials x n_bins` 配列を返します。ここで、`n_trials` = size(binned_repr, 2) です。
