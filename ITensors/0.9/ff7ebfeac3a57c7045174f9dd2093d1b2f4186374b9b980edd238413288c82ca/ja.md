```
*(As::ITensor...; sequence = default_sequence(), kwargs...)
*(As::Vector{<: ITensor}; sequence = default_sequence(), kwargs...)
contract(As::ITensor...; sequence = default_sequence(), kwargs...)
```

ITensorのセットを収縮シーケンスに従って収縮します。

デフォルトのシーケンスは、`ITensors.using_contraction_sequence_optimization()`がtrueの場合は「自動」、そうでない場合は「左結合」（ITensorは左から右に収縮されます）です。

デフォルトは、`ITensors.enable_contraction_sequence_optimization()`および`ITensors.disable_contraction_sequence_optimization()`を使用して変更できます。

カスタムシーケンスの場合、シーケンスは整数`n`を指定する葉を持つ二分木として提供される必要があります。ここで、葉はITensor `As[n]`を指定し、枝は`1`または`2`でインデックス付けされます。つまり、`sequence = Any[Any[1, 3], Any[2, 4]]`のようになります。
