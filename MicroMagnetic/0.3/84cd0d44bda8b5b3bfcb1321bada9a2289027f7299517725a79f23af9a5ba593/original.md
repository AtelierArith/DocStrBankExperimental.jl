```
add_zeeman(sim::AbstractSim, H0::TupleOrArrayOrFunction, ft::Function; name="timezeeman")
```

Add a time varying zeeman to system.

The input `ft` is a function of time `t` and its return value should be a tuple with length 3.

Example:

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
