```
spoil(spin, spoiling, [nothing])
spoil(spinmc, spoiling, [workspace])
```

Simulate gradient or ideal spoiling for the given spin. Returns `(A, B)`, such that `A * M + B` applies spoiling to the magnetization `M`. If `B` is `nothing` (as is the case for `IdealSpoiling`), then `A * M` applies spoiling, and if both `A` and `B` are `nothing` (as is the case for `RFSpoiling`) then there is no spoiling.

For `SpinMC` objects and for `GradientSpoiling` and `RFandGradientSpoiling`, `workspace isa BlochMcConnellWorkspace`. Pass in `nothing` instead to use an approximate matrix exponential to solve the Bloch-McConnell equation.

## Note

This function only simulates gradient or ideal spoiling, *not* RF spoiling. RF spoiling must be implemented by updating the phase of the RF pulse(s) in your sequence from TR to TR.

For an in-place version, see [`spoil!`](@ref). ```
