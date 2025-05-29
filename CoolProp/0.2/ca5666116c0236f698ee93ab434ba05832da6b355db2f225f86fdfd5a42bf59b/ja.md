```
AbstractState_first_saturation_deriv(handle::Clong, of::Clong, wrt::Clong)
```

AbstractStateから、希望するパラメータの整数値を使用して飽和導関数を計算します。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `of`: 導関数が取られるパラメータ
  * `wrt`: このパラメータに関しての導関数

# 例

```julia
julia> as = AbstractState_factory("HEOS", "Water");
julia> AbstractState_update(as, "PQ_INPUTS", 15e5, 0);
julia> AbstractState_first_saturation_deriv(as, get_param_index("Hmolar"), get_param_index("P"))
0.0025636362140578207
```

# 参照

double CoolProp::AbstractState*first*saturation*deriv(const long handle, const long Of, const long Wrt, long* errcode, char* message*buffer, const long buffer_length);
