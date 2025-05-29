```
Batch(batch_size, seq_length)
```

特定のバッチサイズとシーケンス長のために `Batch` のインスタンスを作成します。

これは [`TransformerIntegrator`](@ref) タイプのニューラルネットワークをトレーニングするために使用されます。

オプションで、予測ウィンドウも次のように呼び出すことで指定できます：

```jldoctest
using GeometricMachineLearning

batch_size = 2
seq_length = 3
prediction_window = 2

Batch(batch_size, seq_length, prediction_window)

# output

Batch{:Transformer}(2, 3, 2)
```

ここで、バッチはタイプ `:Transformer` であることに注意してください。
