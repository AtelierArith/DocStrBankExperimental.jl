```
AbstractState_set_fractions(handle::Clong, fractions::Array{Float64})
```

AbstractStateの分率（モル、質量、体積）を設定します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `fractions`: 分率の配列

# 例

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> AbstractState_keyed_output(handle, t)
352.3522212991724
julia> AbstractState_free(handle);
```
