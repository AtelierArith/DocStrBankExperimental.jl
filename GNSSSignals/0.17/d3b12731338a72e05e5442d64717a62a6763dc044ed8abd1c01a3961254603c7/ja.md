```julia
gen_code!(sampled_code, gnss, prn, sampling_frequency)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency
)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase
)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index_shift
)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index_shift,
    maximum_expected_sampling_frequency
)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index_shift,
    maximum_expected_sampling_frequency,
    maximum_expected_doppler
)
gen_code!(
    sampled_code,
    gnss,
    prn,
    sampling_frequency,
    code_frequency,
    start_phase,
    start_index_shift,
    maximum_expected_sampling_frequency,
    maximum_expected_doppler,
    PHASET
)

```

PRN番号 `prn` のシステム `gnss` のために、チップレート `code_frequency` でインプレースでコード信号を生成し、サンプリングレート `sampling_frequency` でサンプリングします。オーバーフローを避けるために、`sampling_frequency` が `code_frequency` より大きいことを確認してください。
