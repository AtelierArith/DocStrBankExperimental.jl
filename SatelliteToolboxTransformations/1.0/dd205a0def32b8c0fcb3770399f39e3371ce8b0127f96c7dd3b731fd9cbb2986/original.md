```
get_Δat(JD::Number) -> Float64
```

Get the accumulated leap seconds (ΔAT) [s] between UTC and International Atomic Time (TAI) in the given `JD`. This function search for ΔAT in the array `ΔAT_Data`.

# Remarks

If `JD` is before `_ΔAT[1, 1]`, then 10 will be returned. **Notice that this can lead to errors.**

If `JD` is after `_ΔAT[end, 1]`, then `_ΔAT[end, 2]` will be returned, because it is not possible yet to predict when leap seconds will be added.
