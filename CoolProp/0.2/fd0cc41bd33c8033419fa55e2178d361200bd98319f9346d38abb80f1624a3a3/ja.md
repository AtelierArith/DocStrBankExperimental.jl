```
AbstractState_get_mole_fractions_satState(handle::Clong, saturated_state::AbstractString,
                                          fractions::Array{Float64})
```

AbstractStateと希望する飽和状態のモル分率を取得します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `saturated_state`: 状態を指定する文字列（液体または気体）
  * `fractions`: 分率の配列

# 例

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> t = get_param_index("T");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> AbstractState_update(handle, pq_inputs, 101325, 0);
julia> gas_frac = [0.0, 0.0]
julia> AbstractState_get_mole_fractions_satState(handle, "gas", gas_frac)
julia> @show gas_frac
gas_frac = [0.30304421184833846, 0.6969557881516616]
julia> liq_frac = [0.0, 0.0]
julia> AbstractState_get_mole_fractions_satState(handle, "liquid", liq_frac)
julia> @show liq_frac
liq_frac = [0.4, 0.6]
julia> AbstractState_free(handle);
```
