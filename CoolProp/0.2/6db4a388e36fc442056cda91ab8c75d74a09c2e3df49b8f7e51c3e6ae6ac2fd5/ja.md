```
AbstractState_get_fugacity(handle::Clong, i::Integer)
```

種 `i` の fugacity を返します

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `i`: 種のインデックス

# 例

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> AbstractState_get_fugacity(handle, 0)
30227.119385400914
julia> AbstractState_free(handle);
```
