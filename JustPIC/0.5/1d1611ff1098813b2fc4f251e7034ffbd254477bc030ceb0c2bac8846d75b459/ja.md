```
Particles{Backend,N,I,T1,T2} <: AbstractParticles
```

粒子のコレクションを表す構造体です。

# 引数

  * `backend`: 粒子計算に使用されるバックエンド (CPUBackend, CUDABackend, AMDGPUBackend)
  * `coords`: 粒子の座標
  * `index`: アクティブな粒子をフラグ付けするヘルパー配列
  * `nxcell`: セルあたりの初期粒子数
  * `max_xcell`: セルあたりの最大粒子数
  * `min_xcell`: セルあたりの最小粒子数
  * `np`: 粒子の数
