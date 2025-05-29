```julia
coarse_fine_acquire(
    system,
    signal,
    sampling_freq,
    prn;
    interm_freq,
    max_doppler,
    coarse_step,
    fine_step
)

```

PRN `prn`を持つ単一の衛星の粗い取得と細かい取得を、信号`signal`が`sampling_freq`のレートでサンプリングされたシステム`system`で実行します。取得は、粗いステップサイズ`coarse_step`と細かいステップサイズ`fine_step`を使用して、ドップラー周波数を用いた並列コード位相検索として実行されます。
