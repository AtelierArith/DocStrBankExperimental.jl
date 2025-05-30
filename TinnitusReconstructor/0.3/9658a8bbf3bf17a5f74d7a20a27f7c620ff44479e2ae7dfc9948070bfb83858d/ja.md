```
subject_selection_process(stimuli_matrix::AbstractVecOrMat{T}, target_signal::AbstractVector{T}) where {T<:Real}
```

合成された被験者の意思決定プロセスを実行します。事前に計算された刺激の行列 `stimuli_matrix` と `target_signal` を与えられます。`stimuli_matrix` はサイズ `m x n` で、`m` は試行の数、`n` は信号内のサンプルの数です。`target_signal` はサイズ `n` のフラットベクトルまたは `n x 1` の行列です。`n` 次元の応答ベクトル `y` と `stimuli_matrix`、およびビン表現のための `nothing` を返します。
