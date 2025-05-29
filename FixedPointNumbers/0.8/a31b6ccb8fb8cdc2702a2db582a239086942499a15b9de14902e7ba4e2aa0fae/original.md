```
Normed{T <: Unsigned, f} <: FixedPoint{T, f}
```

`Normed{T,f}` maps `Unsigned` integers from `0` to `2^f-1` to the range [0.0, 1.0]. For example, `Normed{UInt8,8}` maps `0x00` to `0.0` and `0xff` to `1.0`.

There are the typealiases for `Normed` in the `NXfY` notation, where `Y` is the number of fractional bits (i.e. `f`), and `X+Y` equals the number of underlying bits used. For example, `N0f8` is aliased to `Normed{UInt8,8}` and `N4f12` is aliased to `Normed{UInt16,12}`.
