```
spectrogram(s, n=div(length(s), 8), noverlap=div(n, 2); onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, window=nothing)
```

信号 `s` のスペクトログラムを、`n` サンプルのセグメントに基づいて計算し、`noverlap` サンプルのオーバーラップを持ち、スペクトログラムオブジェクトを返します。オプションのキーワード引数の説明については [`periodogram`](@ref) を参照してください。
