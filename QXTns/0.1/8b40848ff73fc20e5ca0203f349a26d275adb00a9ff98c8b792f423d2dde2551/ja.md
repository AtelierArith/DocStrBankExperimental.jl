```
replace_with_svd!(tn::TensorNetwork,
                  tensor_id::Symbol,
                  left_indices::Array{<:Index, 1};
                  kwargs...)
```

テンソルネットワーク内のテンソルをそのSVDで置き換える関数です。

'left_indices'に含まれるインデックスは、SVDが実行されるときのテンソルの行インデックスと見なされます。

# キーワード

  * `maxdim::Int`: 保持する特異値の最大数。
  * `mindim::Int`: 保持する特異値の最小数。
  * `cutoff::Float64`: SVDの望ましい切断誤差を設定します。
