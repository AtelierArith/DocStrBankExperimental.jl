```
select_device()
```

ノードローカルMPIランクに対応するデバイス（GPU）を選択し、そのIDを返します。

!!! note "デバイスインデックス"
      * CUDA.jlのデバイスインデックスは0ベースです。
      * AMDGPU.jlのデバイスインデックスは1ベースです。
      * したがって、返されるIDはCUDAの場合は0ベース、AMDGPUの場合は1ベースです。


関連: [`init_global_grid`](@ref)
