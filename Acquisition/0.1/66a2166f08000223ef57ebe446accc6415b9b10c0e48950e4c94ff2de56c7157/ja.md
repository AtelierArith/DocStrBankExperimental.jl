```julia
acquire(
    system,
    signal,
    sampling_freq,
    prn;
    interm_freq,
    max_doppler,
    dopplers
)

```

システム `system` で信号 `signal` をサンプリング周波数 `sampling_freq` でサンプリングして、単一の衛星 `prn` の取得を行います。オプションの引数には、中間周波数 `interm_freq`（デフォルトは0Hz）、最大期待ドップラー `max_doppler`（デフォルトは7000Hz）が含まれます。最大ドップラーがあまりにも不特定の場合は、引数 `dopplers` を使用して、個別のステップサイズを持つドップラー範囲を渡すことができます。
