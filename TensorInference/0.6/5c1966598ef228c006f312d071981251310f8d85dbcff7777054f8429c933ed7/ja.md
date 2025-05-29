```julia
update_evidence!(
    tnet::TensorInference.TensorNetworkModel,
    evidence::Dict
) -> TensorInference.TensorNetworkModel

```

テンソルネットワークモデルの証拠を更新しますが、観測された変数のセットは変更しません！

### 引数

  * `tnet` は [`TensorNetworkModel`](@ref) インスタンスです。
  * `evidence` は新しい証拠であり、キーは既存の証拠のサブセットでなければなりません。
