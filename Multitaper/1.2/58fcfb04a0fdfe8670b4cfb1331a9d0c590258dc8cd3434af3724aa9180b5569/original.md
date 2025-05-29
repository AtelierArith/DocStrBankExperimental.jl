```
tanhtrans(trcsq,ntf)
```

Inverse of the magnitude squared coherence variance stabilizing transform

...

# Arguments

  * `trcsq::Float64`: The transformed squared coherence
  * `ntf::Int64`: the number of tapers use to compute the coherence

...

...

# Outputs

  * The output is a `Float64` indicating the reverse-transformed MSC

...

# Example

If the transformed coherence is 7.3 and 6 dof, the significance is

```julia-repl
julia> invmscsig(tanhtrans(7.3,6),6)
```

If the significance is 0.9 and 6 dof the transformed msc is

```julia-repl
julia> atanhtrans(sqrt(mscsig(0.9,6)),6)
```

See also: [`multispec`](@ref)
