```
CountingAll <: AbstractProperty
CountingAll()
```

オーバーフローなしでセットの総数を正確にカウントします。例えば、[`IndependentSet`](@ref) 問題の場合、独立したセットをカウントします。`PartitionFunction(0.0)` もカウントを行います。こちらの方が効率的ですが、浮動小数点数を使用するため、任意の精度はありません。

  * 対応するテンソル要素の型は `BigInt` です。
  * グラフ上の重みは影響を与えません。
  * BLAS（GPUおよびCPU）とGPUがサポートされています。
