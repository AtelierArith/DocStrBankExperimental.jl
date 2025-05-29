```
gpu_device(device_id::Union{Nothing, Integer}=nothing;
    force::Bool=false) -> AbstractDevice
```

次の基準に基づいてGPUデバイスを選択します：

1. `gpu_backend`の優先設定があり、バックエンドがシステムで機能している場合、そのデバイスが選択されます。
2. そうでない場合、自動選択アルゴリズムが使用されます。`supported_gpu_backends()`で指定された順序で可能なデバイスバックエンドを確認し、最初に機能するバックエンドを選択します。
3. 機能するGPUデバイスがない場合、かつ`force`が`false`の場合、`cpu_device()`が呼び出されます。
4. 何も機能しない場合、エラーがスローされます。

## 引数

  * `device_id::Union{Nothing, Integer}`: 選択するデバイスID。`nothing`の場合、最後に選択されたデバイスを返すか、選択されたデバイスがない場合は自動選択を実行し、`CUDA.device()`または`AMDGPU.device()`などを使用して現在のデバイスを選択します。`Integer`の場合、指定されたIDのデバイスを選択します。これは`1`-インデックスであり、`0`-インデックスの`CUDA.jl`とは対照的です。例えば、`id = 4`は`CUDA.device!(3)`に対応します。

!!! warning
    `device_id`は`CUDA`および`AMDGPU`バックエンドにのみ適用されます。`Metal`、`oneAPI`および`CPU`バックエンドの場合、`device_id`は無視され、警告が表示されます。


!!! warning
    `gpu_device`は、CUDAデバイスを選択しません。CUDA.jlとcuDNN.jlの両方がロードされている場合に限ります。これは、深層学習操作が正しく機能することを保証するためです。それでも、cuDNNがロードされていない場合でも、手動で`CUDADevice`オブジェクトを作成して使用することができます（例：`dev = CUDADevice()`）。


## キーワード引数

  * `force::Bool`: `true`の場合、機能するGPUデバイスが見つからないとエラーがスローされます。
