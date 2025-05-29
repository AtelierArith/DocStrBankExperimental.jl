```
add_zeeman(sim::AbstractSim, H0::TupleOrArrayOrFunction, ft::Function; name="timezeeman")
```

システムに時間変化するゼーマンを追加します。

入力 `ft` は時間 `t` の関数であり、その戻り値は長さ3のタプルである必要があります。

例:

```julia
  function time_fun(t)
    w = 2*pi*2.0e9
    return (sin(w*t), cos(w*t), 0)
  end

  function spatial_H(i, j, k, dx, dy, dz)
    H = 1e3
    if i<=2
        return (H, H, 0)
    end
    return (0, 0, 0)
  end

  add_zeeman(sim, spatial_H, time_fun)
```
