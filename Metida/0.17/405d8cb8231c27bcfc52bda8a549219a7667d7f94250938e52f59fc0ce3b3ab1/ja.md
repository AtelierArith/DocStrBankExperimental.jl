```
rand!(v::AbstractVector, lmm::LMM) = rand!(default_rng(), v, lmm, lmm.result.theta, lmm.result.beta)
```

フィットした'lmm'モデルのランダム応答ベクトルを生成し、結果を`v`に格納します。
