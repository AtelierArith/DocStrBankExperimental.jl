```
Fixed{T <: Signed, f} <: FixedPoint{T, f}
```

`Fixed{T,f}` maps `Signed` integers from `-2^f` to `2^f` to the range [-1.0, 1.0]. For example, `Fixed{Int8,7}` maps `-128` to `-1.0` and `127` to `127/128 ≈ 0.992`.

There are the typealiases for `Fixed` in the `QXfY` notation, where `Y` is the number of fractional bits (i.e. `f`), and `X+Y+1` equals the number of underlying bits used (`+1` means the sign bit). For example, `Q0f7` is aliased to `Fixed{Int8,7}` and `Q3f12` is aliased to `Fixed{Int16,12}`.
