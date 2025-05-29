```julia
gen_code(num_samples, gnss, prn, sampling_frequency)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency
)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase
)
gen_code(
    num_samples,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index
)

```

PRN番号 `prn` のシステム `gnss` のコード信号を、チップレート `code_frequency` で生成し、サンプリングレート `sampling_frequency` でサンプリングします。オーバーフローを避けるために、`sampling_frequency` が `code_frequency` より大きいことを確認してください。
