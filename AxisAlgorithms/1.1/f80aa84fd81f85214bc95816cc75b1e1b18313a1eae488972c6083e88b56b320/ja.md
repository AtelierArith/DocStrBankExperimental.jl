`A_mul_B_md!(dest, M, src, dim)` は、次元 `dim` に沿った `src` のスライス `x` に対して `M*x` を計算し、その結果を `dest` に格納します。`M` は `AbstractMatrix` でなければなりません。これは、インプレースのナイーブアルゴリズムを使用します。
