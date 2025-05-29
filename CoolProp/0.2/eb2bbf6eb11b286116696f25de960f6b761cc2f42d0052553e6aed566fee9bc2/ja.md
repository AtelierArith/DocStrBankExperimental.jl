```
AbstractState_update(handle::Clong, input_pair::Clong, value1::Real, value2::Real)
AbstractState_update(handle::Clong, input_pair::AbstractString, value1::Real, value2::Real)
```

AbstractStateの状態を更新します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `input_pair::Clong`: get*input*pair_index(param::AbstractString)から取得した入力ペアの整数値
  * `input_pair::AbstractString`: 入力ペアの名前
  * `value1`: 最初の入力値
  * `value2`: 2番目の入力値

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
