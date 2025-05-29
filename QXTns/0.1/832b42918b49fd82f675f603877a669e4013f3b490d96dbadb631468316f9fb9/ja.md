```
decompose_tensor!(tn::TensorNetwork,
                  tensor_id::Symbol,
                  left_indices::Array{<:Index, 1};
                  contract_S_with::Symbol=:V,
                  kwargs...)
```

テンソネットワーク内のテンソルをSVDを使用して分解する関数です。

# キーワード

  * `contract_S_with::Symbol=:V`: 特異値の行列を吸収すべき行列
  * `maxdim::Int`: 保持する特異値の最大数。
  * `mindim::Int`: 保持する特異値の最小数。
  * `cutoff::Float64`: SVDの望ましい切断誤差を設定します。
