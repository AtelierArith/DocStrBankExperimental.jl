```
set_backend(backend="cuda")
```

MicroMagneticのバックエンドを設定します。この関数を使用すると、MicroMagneticシミュレーションのバックエンドを指定できます。

利用可能なオプションとそれに対応するハードウェアおよびバックエンドは以下の通りです：

| オプション                | ハードウェア     | バックエンド                     |
|:-------------------- |:---------- |:-------------------------- |
| "cpu"                | CPU        | `KernelAbstractions.CPU()` |
| "cuda" または "nvidia"  | NVIDIA GPU | `CUDA.CUDABackend()`       |
| "amd" または "roc"      | AMD GPU    | `AMDGPU.ROCBackend()`      |
| "oneAPI" または "intel" | Intel GPU  | `oneAPI.oneAPIBackend()`   |
| "metal" または "apple"  | Apple GPU  | `Metal.MetalBackend()`     |

# 例

バックエンドをCUDA（NVIDIA GPU）に設定するには：

```julia
using MicroMagnetic
using CUDA
```

バックエンドをCPU/CUDAに設定するには：

```
set_backend("cpu")
set_backend("cuda")
```
