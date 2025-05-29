```
FastApproximation <: Kernels.EvaluationMode
```

カーネルを効率的に評価するために、高速近似またはアルゴリズムを使用します。

評価タイプは実際のカーネルによって異なります：

  * [`KaiserBesselKernel`](@ref) および [`BackwardsKaiserBesselKernel`](@ref) の場合、これはFINUFFTから強くインスパイアされた高速な区分多項式近似を使用します；
  * [`GaussianKernel`](@ref) の場合、これはGreengard & Lee（SIAM Rev. 2004）によって提案された高速ガウスグリディングアルゴリズムを使用します；
  * [`BSplineKernel`](@ref) の場合、これは現在[`Direct`](@ref)評価と同じです。

最初の2つのケースでは、一般的にCPU変換に対して[`Direct`](@ref)評価よりも速くなります。

GPUでは必ずしもそうではなく、結果は実際に使用されるGPUによって異なる場合があります。たとえば、Nvidia A100では、`KaiserBesselKernel`の`Direct`評価（ベッセル関数を含む）は多項式近似を上回るようで、`BackwardsKaiserBesselKernel`（`sinh`関数を含む）よりも少し速いようです。
