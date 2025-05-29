```
log!(F::VectorField, m1::DAMap; work::Tuple{DAMap,DAMap,DAMap,VectorField,VectorField}=prep_log_work(m1), work_Q::Union{Quaternion,Nothing}=prep_work_Q(F))
```

Computes the log of the map `m1` - that is, calculates the `VectorField` `F` that  would represent the map `m1` as a Lie exponent `exp(F)` - and stores the result in `F`. The map `m1` should be close to the identity for this to converge quickly.

### Keyword Arguments

  * `work` – Tuple of 3 `DAMap`s of the same type as `m1` followed by 2 `VectorField`S
  * `work_Q`   – `Quaternion{T}` if spin is included in the vector field, else `nothing`
