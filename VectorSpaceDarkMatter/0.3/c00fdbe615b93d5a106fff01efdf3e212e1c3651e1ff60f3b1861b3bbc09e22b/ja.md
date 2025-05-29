```
ProjectedF{A, B}(fnlm::Matrix{A}, lm, radial_basis::B)
```

$$
\langle f | n \ell m \rangle
$$

の係数と、それらを計算するために使用された放射基底を格納します。角部分には球面調和関数が使用されていると仮定します。`A` は `fnlm` 係数を格納する行列の要素型（`Float64` または `Measurement` のいずれかである必要があります）。`B` は放射基底の型です。`lm` は `fnlm` 行列の `(ell,m)` のベクトルを格納します：`fnlm` は `(ell,m) = lm[i]` に対応する `[n+1,i]` としてインデックス付けされます。
