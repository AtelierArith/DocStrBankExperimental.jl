```
has_gpu()
```

TensorFlowバックエンドがCUDA GPUを使用しているかどうかを確認します。GPU実装を持つ演算子はGPUデバイスで実行されます。 参照してください [`get_gpu`](@ref)

!!! note
    ADCMEは、GPUが利用可能な場合、自動的にGPUを使用します。GPUを無効にするには、ADCMEをインポートする前に環境変数 `ENV["CUDA_VISIBLE_DEVICES"]=""` を設定してください。

