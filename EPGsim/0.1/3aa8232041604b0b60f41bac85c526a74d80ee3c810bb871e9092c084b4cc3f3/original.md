```
EPGStates{T <: Real}
```

Stores the EPG states in 3 vectors Fp,Fn and Z.

# Constructors :

```
EPGStates(Fp::Vector{Complex{S}},Fn::Vector{Complex{S}},Z::Vector{Complex{S}}) where {S <: Real}
EPGStates(Fp::T=0,Fn::T=0,Z::T=1) where T <: Number
```

# Fields

  * `Fp::Vector{Complex{T}}`
  * `Fn::Vector{Complex{T}}`
  * `Z::Vector{Complex{T}}`

# Related functions

  * `getStates(E::EPGStates)` : extract EPG states as matrix 3xN
