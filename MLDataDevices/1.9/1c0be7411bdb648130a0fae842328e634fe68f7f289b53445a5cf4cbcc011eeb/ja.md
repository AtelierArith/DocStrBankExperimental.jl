```
DeviceIterator(dev::AbstractDevice, iterator)
```

提供された `iterator` を `iterate` を介して反復する `DeviceIterator` を作成します。各反復の際に、現在のバッチがデバイス `dev` にコピーされ、前の反復は GPU メモリから解放可能としてマークされます（CPU デバイスの場合は no-op です）。

変換は `dev(<item from iterator>)` と同じ意味論に従います。

!!! tip "CUDA.CuIterator との類似性"
    設計のインスピレーションは `CUDA.CuIterator` から得られ、他のバックエンドやより複雑なイテレータ（`Functors` を使用）で動作するように一般化されました。


!!! tip "`MLUtils.DataLoader`"
    `dev(::MLUtils.DataLoader)` を呼び出すと、データローダーが `DeviceIterator` と同じ意味論を使用するように自動的に変換されます。これは、データローダーを直接ループしてデータをデバイスに転送するよりも一般的に好まれます。


## 例

以下は NVIDIA GPU を搭載したコンピュータで実行されました。

```julia-repl
julia> using MLDataDevices, MLUtils

julia> X = rand(Float64, 3, 33);

julia> dataloader = DataLoader(X; batchsize=13, shuffle=false);

julia> for (i, x) in enumerate(dataloader)
           @show i, summary(x)
       end
(i, summary(x)) = (1, "3×13 Matrix{Float64}")
(i, summary(x)) = (2, "3×13 Matrix{Float64}")
(i, summary(x)) = (3, "3×7 Matrix{Float64}")

julia> for (i, x) in enumerate(CUDADevice()(dataloader))
           @show i, summary(x)
       end
(i, summary(x)) = (1, "3×13 CuArray{Float32, 2, CUDA.DeviceMemory}")
(i, summary(x)) = (2, "3×13 CuArray{Float32, 2, CUDA.DeviceMemory}")
(i, summary(x)) = (3, "3×7 CuArray{Float32, 2, CUDA.DeviceMemory}")
```
