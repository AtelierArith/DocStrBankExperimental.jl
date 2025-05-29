```
Antidot{T<:AbstractFloat} <: Circular{T}
```

Disk-like obstacle that allows propagation both inside and outside of the disk (mutable type). Used in ray-splitting billiards.

### Fields:

  * `c::SVector{2,T}` : Center.
  * `r::T` : Radius.
  * `pflag::Bool` : Flag that keeps track of where the particle is currently propagating (`pflag` = propagation-flag). `true` stands for *outside* the disk, `false` for *inside* the disk. Defaults to `true`.
  * `name::String` : Name of the obstacle given for user convenience. Defaults to "Antidot".
