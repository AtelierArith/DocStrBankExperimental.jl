```
abstract type SHTnsType
```

SHTnsTypeは球面調和変換タイプのための抽象型です。すべてのサブタイプは以下のキーワード引数を含みます：

  * `contiguous_lat::Bool=true`
  * `contiguous_phi::Bool=false`
  * `padding::Bool=false`
  * `gpu::Bool=false`
  * `southpolefirst::Bool=false`
  * `float32::Bool=false`
