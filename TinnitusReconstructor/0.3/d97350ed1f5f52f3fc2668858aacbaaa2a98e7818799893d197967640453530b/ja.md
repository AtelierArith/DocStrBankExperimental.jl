```
binnedrepr2wav(s::BS, binned_repr::AbstractVecOrMat{T}; min_db::Real = -20) where {BS <: BinnedStimgen, I <: Integer, T <: Real}
```

ビン化された表現を波形に変換し、`min_db` と 0 の間に再スケーリングします。

波形のみを返します。
