```
AbstractState_set_binary_interaction_double(handle::Clong, i::Int, j::Int, parameter::AbstractString, value::Float64)
```

異なる混合物モデルのための二元相互作用パラメータを設定します。例："linear", "Lorentz-Berthelot"

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `i`: 二元ペアの最初の流体のインデックス
  * `j`: 二元ペアの二番目の流体のインデックス
  * `parameter`: パラメータの名前を持つ文字列。例："betaT", "gammaT", "betaV", "gammaV"
  * `value`: 二元相互作用パラメータの値

# 例

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> AbstractState_set_binary_interaction_double(handle, 0, 1, "betaT", 0.987);
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> AbstractState_keyed_output(handle, t)
349.32634425309755
julia> AbstractState_free(handle);
```
