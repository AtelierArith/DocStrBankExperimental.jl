```
surrogate_model(plan::AbstractArray{T,2}, samples::AbstractArray{T,2}; options=Options()) where T
```

最適化された放射基底関数補間に基づくサロゲートモデル関数を返します。提供されたオプションに応じて、カーネル、カーネル幅、および入力データのスケーリングが最適化されます。

...

# 引数

  * `plan::AbstractArray{T,2}`:    各列が1つの点の位置に対応するサンプル位置。   `size(plan) = (num_dimensions,num_samples)`。
  * `samples::AbstractArray{T,2}`:   各サンプル位置での関数値。各列には対応するプラン位置からの1つの値が含まれます。 `size(samples) = (1,num_samples)`。
  * `options=Options()`:    サロゲート最適化をカスタマイズするために利用可能なすべてのオプション。

...
