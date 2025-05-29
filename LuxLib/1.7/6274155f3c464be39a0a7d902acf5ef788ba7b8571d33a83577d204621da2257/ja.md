```
internal_operation_mode(xs::Tuple)
internal_operation_mode(x::AbstractArray)
```

与えられた配列の内部操作モードを返します。これは、シンプルなJuliaブロードキャスティング、カーネル抽象、ループベクトル化など、異なるバックエンドを使用してカスタム実装を定義するのに役立ちます。

現在サポートされているモードは次のとおりです：

  * `GenericBroadcastOp`: これはほとんどのタイプのフォールバックです。次のタイプに対しては、これが推奨されるモードです：

      * `fast_scalar_indexing`が`False`に設定されている配列。
      * 静的配列
      * ReverseDiff配列
      * Tracker配列
      * ForwardDiff.Dual配列
      * 複素配列
  * `GPUBroadcastOp{dev}`: `dev`が`get_device_type(xs)`から取得されるGPU配列。このオプションのディスパッチは、できれば`KernelAbstractions`または専門のベンダーディスパッチを使用するべきです。
  * `LoopedArrayOp`: SIMDループを使用して最適化できるCPU配列、理想的には`LoopVectorization.jl`または`Polyester.jl`を使用します。
