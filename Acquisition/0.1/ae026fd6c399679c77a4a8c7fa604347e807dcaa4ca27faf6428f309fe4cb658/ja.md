```julia
coarse_fine_acquire(
    system,
    signal,
    sampling_freq,
    prns;
    interm_freq,
    max_doppler,
    coarse_step,
    fine_step
)

```

複数の衛星 `prns` の粗い取得と細かい取得を、信号 `signal` をサンプリング周波数 `sampling_freq` でサンプリングしたシステム `system` で実行します。取得は、粗いステップサイズ `coarse_step` と細かいステップサイズ `fine_step` を使用して、ドップラー周波数を用いた並列コード位相検索として実行されます。
