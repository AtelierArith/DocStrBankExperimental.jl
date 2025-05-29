```
Pollen3D(sv = (128, 128, 128), dphi::Float64=0.0, dtheta::Float64=0.0)
```

Create a 3D representation of a pollen grain.

# Arguments

  * `sv::Tuple`: A tuple of three integers representing the size of the volume in which the pollen grain will be created. Default is (128, 128, 128).
  * `dphi::Float64`: A float representing the phi angle offset in radians. Default is 0.0.
  * `dtheta::Float64`: A float representing the theta angle offset in radians. Default is 0.0.

# Returns

  * `ret::Array{Float64}`: A 3D array representing the pollen grain.

# Example

```jldoctest
Pollen3D((256, 256, 256), 0.0, 0.0)
```
