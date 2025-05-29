```
lift(f::T, Kt) where T <: Union{zzModPolyRingElem, ZZModPolyRingElem, fpPolyRingElem} -> Generic.Poly{PadicFieldElem}
```

剰余環のすべての係数を持ち上げる多項式の持ち上げを計算します。
