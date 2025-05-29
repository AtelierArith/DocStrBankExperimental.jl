`CudaOffloadFactorization()`

CPUベースの計算をGPUで加速するために使用されるオフロード技術です。データ転送コストを上回るために、十分に大きな`A`が必要です。

!!! note
    このソルバーを使用するには、パッケージCUDA.jlを追加する必要があります。すなわち、`using CUDA`

