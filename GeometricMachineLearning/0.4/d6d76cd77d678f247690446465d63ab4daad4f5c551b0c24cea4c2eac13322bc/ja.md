```
apply_section!(Y::AT, λY::GlobalSection{T, AT}, Y₂::AT) where {T, AT<:StiefelManifold{T}}
```

`λY`を`Y₂`に適用し、その結果を`Y`に格納します。

これは[`apply_section`](@ref)のインプレースバージョンです。
