```julia
canonicalize_clip!(
    state::QuantumClifford.AbstractStabilizer;
    phases
) -> QuantumClifford.AbstractStabilizer

```

Fix the clipped gauge of a stabilizer (in place).

Assumes the input is a valid full-rank stabilizer (all operators commute and have real phases).

```jldoctest
julia> s = S"- X_ZX_X
             + XXYZ__
             - YZ_Z_X
             - XZX__Y
             + _Z_Y_Y
             - ____Z_";


julia> canonicalize_clip!(s)
- X_XY__
+ YZY___
+ _XZX__
- _ZYX_Z
- __YZ_X
- ____Z_
```

If `phases=false` is set, the canonicalization does not track the phases in the tableau, leading to a significant speedup.

Introduced in [nahum2017quantum](@cite), with a more detailed explanation of the algorithm in Appendix A of [li2019measurement](@cite)

See also: [`canonicalize!`](@ref), [`canonicalize_rref!`](@ref), [`canonicalize_gott!`](@ref).
