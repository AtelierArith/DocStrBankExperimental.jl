## `boolean_indicator`

```julia
boolean_indicator(f::AbstractArray)
boolean_indicator(f::AbstractGPUArray)
boolean_indicator(f::BitArray)
```

ブールインジケーター配列の浮動小数点表現を作成します。ここで `0` は背景を表し、`1` は前景を表します。この関数は論理配列を浮動小数点配列に変換し、前景値（論理 `1`）は `0.0f0`（`0` の浮動小数点表現）としてマークされ、背景値（論理 `0`）は大きな浮動小数点数 `1.0f10` でマークされます。この表現は、前景と背景を区別するための距離変換操作で便利です。

#### 引数

  * `f`: ブール値の配列またはブール値の `AbstractGPUArray` で、`true` は前景を、`false` は背景を示します。

#### 戻り値

  * `f` と同じ次元の浮動小数点配列で、前景値は `0.0f0` に設定され、背景値は `1.0f10` に設定されます。

#### パフォーマンス

  * `f` が `BitArray` の場合、変換は LoopVectorization.jl を使用して潜在的なスピードアップを図ります。警告チェック引数はパフォーマンス上の理由から無効にされています。
  * `f` が `AbstractGPUArray` の場合、計算はカスタムカーネル `boolean_indicator_kernel` を使用してGPUにオフロードされ、互換性のあるハードウェアでの大幅なスピードアップが期待されます。

#### 例

```julia
f = BitArray([true, false, true, false])
f_float = boolean_indicator(f)
# f_float は Float32[0.0f0, 1.0f10, 0.0f0, 1.0f10] になります

f_gpu = CUDA.zeros(Bool, 10) # CUDA.jl が GPU 配列に使用されていると仮定
f_gpu[5] = true
f_float_gpu = boolean_indicator(f_gpu)
# f_float_gpu は5番目の要素が 0.0f0 で他が 1.0f10 の GPU 配列になります
```

#### 注意事項

  * `1.0f10` を大きな数として選択するのは任意であり、特定のアプリケーションに応じて調整可能です。
  * `f` が `AbstractGPUArray` の場合、`boolean_indicator_kernel` カーネル関数が GPU での並列処理を行うために使用されます。
  * `KernelAbstractions.synchronize(backend)` 呼び出しは、結果を返す前にすべての GPU 操作が完了することを保証します。
