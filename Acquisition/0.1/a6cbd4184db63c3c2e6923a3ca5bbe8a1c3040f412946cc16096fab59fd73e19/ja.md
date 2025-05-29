```julia
acquire!(
    acq_plan,
    signal,
    prns;
    interm_freq,
    doppler_offset,
    noise_power
)

```

この取得関数は、事前に定義された取得プランを使用して計算時間を短縮します。これは、連続して複数回取得を計算する必要がある場合に便利です。
