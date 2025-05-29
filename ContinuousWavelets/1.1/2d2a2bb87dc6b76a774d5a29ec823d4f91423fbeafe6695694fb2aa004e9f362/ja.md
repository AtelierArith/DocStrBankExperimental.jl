```
 wave = cwt(Y::AbstractArray{T,N}, c::CWT{W, S, WT}, daughters, rfftPlan =
         plan_rfft([1]), fftPlan = plan_fft([1])) where {N, T<:Real,
                                                         S<:Real,
                                                         U<:Number,
                                                         W<:WaveletBoundary,
                                                         WT<:ContWaveClass}
```

最初の軸に沿って平均化を伴う連続ウェーブレット変換を返します。 `wave`は(signalLength)×(nscales+1)×(前の次元)の型`T`の`Y`です。 `averagingLength`は、平均化関数によって置き換えられるオクターブ（2の累乗）の数を定義します。これは`averagingType`の形式を持ち、`Father()`または`Dirac()`のいずれかになります。`Father()`の場合、ウェーブレットと同じ形式を使用しますが、`Dirac`は定数ウィンドウを使用します。サンプリング情報がある場合は、波をδt^(1/p)でスケーリングする必要があります。デフォルトの仮定は、サンプリングレートが2kHzであることです。
