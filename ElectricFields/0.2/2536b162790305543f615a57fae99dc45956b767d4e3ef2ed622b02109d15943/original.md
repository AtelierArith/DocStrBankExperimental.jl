```
DispersedField(f::DispersedField, de)
```

Stacking another [`DispersiveElement`](@ref) `de` onto an already dispersed field `f` is accomlished by multiplying the transfer functions together, with the earliest applied as the right-most factor:

$$
H(\omega) = H_n(\omega) ... H_3(\omega)H_2(\omega)H_1(\omega).
$$
