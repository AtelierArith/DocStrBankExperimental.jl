```
binnedrepr2wav(s::BS, binned_repr::AbstractVecOrMat{T}, mult, binrange,
new_n_bins::I = 256) where {BS <: BinnedStimgen, I <: Integer, T <: Real}
```

バイナリ表現を波形に変換します。解像度を補間によって向上させ（`new_n_bins`）、ピークをシャープにし（`mult`）、ダイナミックレンジを再スケーリングします（`binrange`）。

波形と関連する周波数スペクトルを返します。
