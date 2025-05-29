```
densratiofunc(x_nu, x_de, dre; [optlib])
```

Similar to [`densratio`](@ref), but return a function `r(x) = p_nu(x) / p_de(x)` that can be evaluated at a new unseen sample `x`.

See also [`densratio`](@ref).

### Notes

Only some estimators define a ratio function that can be evaluated outside `x_de`.
