```
enableAcceleration(tsg::TasmanianSG, acceleration_type, GPUID = 0)
```

加速バックエンドライブラリや拡張機能（BLASやCUDAなど）の使用を有効にします。各加速タイプには対応するCMakeコンパイルオプションが必要であり、そうでない場合はバックエンドは最も近い利用可能なオプションにフォールバックします。

sAccelerationType: 文字列

'none'       コアフォールバックモード、逐次実装に依存します       Tasmanian*ENABLE*OPENMPでコンパイルされている場合、       単純な "omp parallel for" を使用して複数のCPUコアを活用します

'cpu-blas'       バッチ評価の加速のためにBLASレベル2および3の関数を使用します       Tasmanian*ENABLE*BLAS=ONが必要です       これは利用可能な場合のデフォルトモードです

'gpu-default'       CUDAカーネル、cuBlas、cuSparseおよびMAGMAライブラリを使用して       加速された行列演算を行います。例：cublasDgemm       詳細についてはTasGrid::TypeAccelerationを参照してください

'gpu_cublas'       NvidiaのcuBlasおよびcuSparseライブラリを使用します

'gpu-cuda'       加速された線形代数ライブラリに加えてカスタムCUDAカーネルを使用します

'gpu-magma'       デフォルトのNvidiaライブラリの代わりにカスタムCUDAカーネルとMAGMAライブラリを使用します

GPUID: 整数       使用するGPUデバイスを示します。Noneに設定されている場合、       最初にデバイスゼロが使用されるか、setGPUID()で設定されたデバイスが使用されます。
