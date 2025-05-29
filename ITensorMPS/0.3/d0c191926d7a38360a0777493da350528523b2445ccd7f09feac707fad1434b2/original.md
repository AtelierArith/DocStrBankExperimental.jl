```
MPS([::Type{ElT} = Float64, ]sites; linkdims=1)
```

Construct an MPS filled with Empty ITensors of type `ElT` from a collection of indices.

Optionally specify the link dimension with the keyword argument `linkdims`, which by default is 1.

In the future we may generalize `linkdims` to allow specifying each individual link dimension as a vector, and additionally allow specifying quantum numbers.
