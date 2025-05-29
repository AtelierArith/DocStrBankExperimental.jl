```
getoffset(TT, TDB, second, fraction[, eop])
```

Return the offset between [`TT`](@ref) and [`TDB`](@ref) for the current epoch (`second` after J2000 and `fraction`) in seconds. This routine is accurate to ~40 microseconds over the interval 1900-2100.

!!! note
    An accurate transformation between TDB and TT depends on the trajectory of the observer. For two observers fixed on Earth's surface the quantity TDB-TT can differ by as much as ~4 microseconds. See [`here`](@ref getoffset(::TerrestrialTime, ::BarycentricDynamicalTime, second, fraction, elong, u, v)).


# Example

```jldoctest; setup = :(using AstroTime)
julia> getoffset(TT, TDB, 0, 0.0)
-7.273677619130569e-5
```

### References

  * [https://www.cv.nrao.edu/~rfisher/Ephemerides/times.html#TDB](https://www.cv.nrao.edu/~rfisher/Ephemerides/times.html#TDB)
  * [Issue #26](https://github.com/JuliaAstro/AstroTime.jl/issues/26)
