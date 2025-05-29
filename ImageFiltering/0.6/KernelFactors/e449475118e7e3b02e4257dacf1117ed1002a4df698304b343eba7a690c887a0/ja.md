`KernelFactors`は、各フィルタリングカーネルをその因子の形で格納するモジュールです。サポートされているカーネルは次のとおりです：

  * `sobel`
  * `prewitt`
  * `ando3`、`ando4`、および`ando5`（後者は2dのみ）
  * `scharr`
  * `bickley`
  * `gaussian`
  * `IIRGaussian`（近似ガウスフィルタリング、大きなσでも高速）

参照：[`Kernel`](@ref)。
