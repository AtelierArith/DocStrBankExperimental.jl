```
TauSampling(basis; sampling_points=default_tau_sampling_points(basis), factorize=true)
```

`TauSampling`オブジェクトを構築します。指定されていない場合、`sampling_points`は虚時間における最高次基底関数の極値として選択されます。これは、このサイズに関して条件付けに対してほぼ最適であることが判明しています（数パーセント以内）。`factorize`は、SVD分解が計算されるかどうかを制御します。
