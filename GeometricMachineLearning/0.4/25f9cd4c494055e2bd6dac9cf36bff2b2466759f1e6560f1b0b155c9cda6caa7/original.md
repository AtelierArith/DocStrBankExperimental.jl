```
Batch(batch_size, seq_length)
```

Make an instance of `Batch` for a specific batch size and a sequence length.

This is used to train neural networks of [`TransformerIntegrator`](@ref) type.

Optionally the prediction window can also be specified by calling:

```jldoctest
using GeometricMachineLearning

batch_size = 2
seq_length = 3
prediction_window = 2

Batch(batch_size, seq_length, prediction_window)

# output

Batch{:Transformer}(2, 3, 2)
```

Note that here the batch is of type `:Transformer`.
