```
unnatural(targetUnit, q)
```

Convert a quantity `q` to units specified by `targetUnits` automatically inserting whatever  factors  of `ħ`, `c`, `ϵ₀` and `kb` are required to make the conversion work.

Examples:

```
julia> unnatural(u"m", 5.067730759202785e6u"eV^-1")
1.0 m

julia> unnatural(u"m/s", 1)
2.99792458e8 m s^-1

julia> unnatural(u"K", 1u"eV")
11604.522060401006 K
```
