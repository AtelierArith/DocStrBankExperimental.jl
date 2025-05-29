```julia
acquire(
    system,
    signal,
    sampling_freq,
    prns;
    interm_freq,
    max_doppler,
    dopplers
)

```

複数の衛星を `prns` でシステム `system` において、信号 `signal` をサンプリング周波数 `sampling_freq` で取得します。オプション引数には、中間周波数 `interm_freq`（デフォルトは0Hz）、最大期待ドップラー `max_doppler`（デフォルトは7000Hz）があります。最大ドップラーがあまりにも不明確な場合は、引数 `dopplers` を使用して個別のステップサイズを持つドップラー範囲を渡すことができます。
