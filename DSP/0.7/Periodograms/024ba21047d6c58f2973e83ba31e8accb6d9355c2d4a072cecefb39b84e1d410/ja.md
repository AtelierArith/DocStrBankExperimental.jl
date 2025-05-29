```
welch_pgram(s, n=div(length(s), 8), noverlap=div(n, 2); onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, window=nothing)
```

信号 `s` のウェルチ周期グラムを、`n` サンプルのセグメントに基づいて計算し、`noverlap` サンプルのオーバーラップを持ち、周期グラムオブジェクトを返します。バートレット周期グラムの場合は、`noverlap=0` に設定します。オプションのキーワード引数の説明については [`periodogram`](@ref) を参照してください。
