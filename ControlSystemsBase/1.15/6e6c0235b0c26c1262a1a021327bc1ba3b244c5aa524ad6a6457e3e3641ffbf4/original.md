```
C, kp, ki = placePI(P, ω₀, ζ; form=:standard)
```

Selects the parameters of a PI-controller such that the poles of  closed loop between `P` and `C` are placed to match the poles of  `s^2 + 2ζω₀s + ω₀^2`.

The parameters can be returned as one of several common representations  chose by `form`, the options are

  * `:standard` - $K_p(1 + 1/(T_i s))$
  * `:series` - $K_c(1 + 1/(τ_i s))$ (equivalent to above for PI controllers)
  * `:parallel` - $K_p + K_i/s$

`C` is the returned transfer function of the controller and `params`  is a named tuple containing the parameters. The parameters can be accessed as `params.Kp` or `params["Kp"]` from the named tuple, or they can be unpacked using `Kp, Ti, Td = values(params)`.

See also [`loopshapingPI`](@ref)
