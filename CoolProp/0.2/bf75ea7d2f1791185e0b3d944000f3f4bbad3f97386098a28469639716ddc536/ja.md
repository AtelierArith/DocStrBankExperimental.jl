```
AbstractState_first_partial_deriv(handle::Clong, of::Clong, wrt::Clong, constant::Clong)
```

抽象状態から均質相における第一部分導関数を、希望するパラメータの整数値を使用して計算します。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `of`: 導関数が取られるパラメータ
  * `Wrt`: このパラメータに関しての導関数
  * `Constant`: 導関数の影響を受けないパラメータ

# 例

```julia
julia> as = AbstractState_factory("HEOS", "Water");
julia> AbstractState_update(as, "PQ_INPUTS", 15e5, 0);
julia> AbstractState_first_partial_deriv(as, get_param_index("Hmolar"), get_param_index("P"), get_param_index("S"))
2.07872526058326e-5
julia> AbstractState_first_partial_deriv(as, get_param_index("Hmolar"), get_param_index("P"), get_param_index("D"))
5.900781297636475e-5
```

# 参照

double CoolProp::AbstractState*first*partial*deriv(const long handle, const long Of, const long Wrt, const long Constant, long* errcode, char* message*buffer, const long buffer_length); ```
