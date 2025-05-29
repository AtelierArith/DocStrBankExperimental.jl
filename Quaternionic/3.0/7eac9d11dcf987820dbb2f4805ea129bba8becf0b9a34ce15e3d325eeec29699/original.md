```
unflip(q, [dim=1])
unflip!(q, [dim=1])
```

Flip the signs of successive quaternions along dimension `dim` so that they are as continuous as possible.

If `q` represents a series of rotations, the sign of each element is arbitrary. However, for certain purposes — such as interpolation and differentiation — the continuity of the quaternions matters, and so we want the *quaternions* to be as continuous as possible without changing the *rotations* that they represent.

# Examples

```jldoctest
julia> q = [imx, -imx, imx, -imx];

julia> unflip(q)
4-element Vector{QuatVec{Int64}}:
  + 1𝐢 + 0𝐣 + 0𝐤
  + 1𝐢 + 0𝐣 + 0𝐤
  + 1𝐢 + 0𝐣 + 0𝐤
  + 1𝐢 + 0𝐣 + 0𝐤
```
