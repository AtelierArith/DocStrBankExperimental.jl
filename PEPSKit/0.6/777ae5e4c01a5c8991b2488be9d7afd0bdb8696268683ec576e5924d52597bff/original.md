```julia
struct FullSVDReverseRule
```

SVD reverse-rule algorithm which uses a modified version of TensorKit's `tsvd!` reverse-rule allowing for Lorentzian broadening and output verbosity control.

## Fields

  * `broadening::Float64`
  * `verbosity::Int64`

## Constructors

```
FullSVDReverseRule(; kwargs...)
```

Construct a `FullSVDReverseRule` algorithm struct from the following keyword arguments:

  * `broadening::Float64=1.0e-13` : Lorentzian broadening amplitude for smoothing divergent term in SVD derivative in case of (pseudo) degenerate singular values.
  * `verbosity::Int=0` : Suppresses all output if `≤0`, prints gauge dependency warnings if `1`, and always prints gauge dependency if `≥2`.
