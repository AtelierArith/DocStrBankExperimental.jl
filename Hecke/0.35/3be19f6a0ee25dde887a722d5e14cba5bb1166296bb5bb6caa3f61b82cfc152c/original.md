```
lift(f::T, Kt) where T <: Union{zzModPolyRingElem, ZZModPolyRingElem, fpPolyRingElem} -> Generic.Poly{PadicFieldElem}
```

Computes a lift of the polynomial lifting every coefficient of the residue ring.
