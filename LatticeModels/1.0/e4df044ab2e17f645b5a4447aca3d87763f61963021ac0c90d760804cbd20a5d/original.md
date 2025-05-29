```
integrate!(tseq::TimeSequence)
```

Integrate the values stored in `tseq` over time using the trapezoidal rule. The new values are written into `tseq`. The first value is set to zero.

## Example

```jldoctest
julia> using LatticeModels

julia> tseq = TimeSequence(0:0.1:10, 0:0.1:10)  # f(t) = t
TimeSequence{Float64} with 101 entry
Timestamps in range 0.0 .. 10.0:
  0.0 => 0.0
  0.1 => 0.1
  0.2 => 0.2
  0.3 => 0.3
  0.4 => 0.4
  0.5 => 0.5
  0.6 => 0.6
  0.7 => 0.7
  0.8 => 0.8
  ⋮

julia> integrate!(tseq)                         # F(t) = t^2 / 2
TimeSequence{Float64} with 101 entry
Timestamps in range 0.0 .. 10.0:
  0.0 => 0.0
  0.1 => 0.005
  0.2 => 0.02
  0.3 => 0.045
  0.4 => 0.08
  0.5 => 0.125
  0.6 => 0.18
  0.7 => 0.245
  0.8 => 0.32
  ⋮
```
