```
baum_welch_multiple_sequences(obs_sequences, hmm_init::HMM[, par; max_iterations, tol])
```

複数の観測シーケンスに対してバウム-ウェルチアルゴリズムを適用します。初期の [`HMM`](@ref) `hmm_init` とパラメータ `par` から始めます。

パラメータは変更されません。
