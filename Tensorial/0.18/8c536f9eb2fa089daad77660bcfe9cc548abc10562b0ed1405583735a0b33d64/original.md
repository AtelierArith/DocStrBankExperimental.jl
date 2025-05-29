`Quaternion` represents $q_w + q_x \bm{i} + q_y \bm{j} + q_z \bm{k}$. The salar part and vector part can be accessed by `q.scalar` and `q.vector`, respectively.

# Examples

```jldoctest
julia> Quaternion(1,2,3,4)
1 + 2𝙞 + 3𝙟 + 4𝙠

julia> Quaternion(1)
1 + 0𝙞 + 0𝙟 + 0𝙠

julia> Quaternion(Vec(1,2,3))
0 + 1𝙞 + 2𝙟 + 3𝙠
```

See also [`quaternion`](@ref).

!!! note
    `Quaternion` is experimental and could change or disappear in future versions of Tensorial.

