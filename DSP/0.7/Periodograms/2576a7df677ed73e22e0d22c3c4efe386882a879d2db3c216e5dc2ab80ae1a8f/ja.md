```
stft(s, n=div(length(s), 8), noverlap=div(n, 2); onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, window=nothing)
```

信号 `s` の STFT を、`n` サンプルのセグメントに基づいて、`noverlap` サンプルのオーバーラップで計算し、STFT コエフィシエントを含む行列を返します。オプションのキーワード引数の説明については [`periodogram`](@ref) を参照してください。
