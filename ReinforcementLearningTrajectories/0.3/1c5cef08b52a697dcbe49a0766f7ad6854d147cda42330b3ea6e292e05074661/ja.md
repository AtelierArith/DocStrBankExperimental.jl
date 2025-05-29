```
NStepBatchSampler{names}(; n, γ, batchsize=32, stacksize=nothing, rng=Random.GLOBAL_RNG)
```

nステップTD学習のフレームワークにおいて、連続する報酬の割引合計をサンプリングするために使用されます。Multiplexedトレースの「次」の要素（次の*状態や次の*行動など）は、バッファ内の最大`n > 1`ステップ後のものになります。報酬は、割引率`γ`を用いた`n`の報酬の割引合計になります。

NStepBatchSamplerは、`stacksize`が1より大きい整数に設定されている場合、n ≥ 1で「スタック」状態をサンプリングするためにも使用できます。これは、(stacksize - 1)の前の状態をサンプリングします。これは、部分的な可観測性のケースで便利であり、例えば状態が`stacksize`の連続したフレームによって近似される場合に役立ちます。
