```Julia
hyperfine(U::UnitSystem) = frequency(9.19263177e9,U)
```

セシウム-133原子の非摂動基底状態超微細遷移周波数 `ΔνCs` (Hz)。

```Julia
julia> hyperfine(Metric) # Hz
9.19263177e9
```
