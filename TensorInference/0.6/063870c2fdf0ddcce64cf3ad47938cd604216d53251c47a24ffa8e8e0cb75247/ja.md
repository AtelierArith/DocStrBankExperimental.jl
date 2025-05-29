```julia
probability(
    tn::TensorInference.TensorNetworkModel;
    usecuda,
    rescale
) -> AbstractArray

```

テンソルネットワークを収束させ、証拠の確率の配列を返します。正確には、返される値は分配関数であり、l1正規化されていない場合があります。

入力テンソルネットワークの `openvars` がゼロの場合、配列のランクはゼロです。それ以外の場合、返される値は周辺確率に対応します。
