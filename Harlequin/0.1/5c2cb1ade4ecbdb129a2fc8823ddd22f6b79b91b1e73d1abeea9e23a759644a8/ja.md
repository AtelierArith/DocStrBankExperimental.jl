```
compute_nobs_matrix!(nobs_matrix::Vector{NobsMatrixElement}, observations::Vector{Observation{T}})
```

`nobs_matrix`のすべての要素を初期化して、KurkiSuonio2009の式(10)のM_p行列にします。TODは、パラメータ`observations`の観測リストから取得されます。
