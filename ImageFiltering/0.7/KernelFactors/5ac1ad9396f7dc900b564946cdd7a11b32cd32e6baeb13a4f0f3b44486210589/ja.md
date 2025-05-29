`KernelFactors`は、各フィルタリングカーネルをその因子の観点から格納するモジュールです。サポートされているカーネルは以下の通りです：

  * `box`
  * `sobel`
  * `prewitt`
  * `ando3`、`ando4`、および`ando5`（後者は2dのみ）
  * `scharr`
  * `bickley`
  * `gaussian`
  * `IIRGaussian`（近似ガウスフィルタリング、大きなσでも高速）

詳細については、[`Kernel`](@ref)を参照してください。
