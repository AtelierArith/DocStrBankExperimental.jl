```
imy
𝐣
```

The quaternionic unit associated with rotation about the `y` axis.  Can also be entered as Unicode bold `𝐣` (which can be input as `\bfj<tab>`).

Note that — just as `im` is a `Complex{Bool}` — `imy` is a `QuatVec{Bool}`, and as soon as you multiply by a scalar of any other number type (e.g., a `Float64`) it will be promoted to a `QuatVec` of that number type, and once you *add* a scalar it will be promoted to a `Quaternion`.

See also [`imx`](@ref) and [`imz`](@ref).

# Examples

```jldoctest
julia> imy * imy
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imy
 + 0.0𝐢 + 1.2𝐣 + 0.0𝐤
julia> 1.2 + 3.4imy
1.2 + 0.0𝐢 + 3.4𝐣 + 0.0𝐤
julia> 1.2 + 3.4𝐣
1.2 + 0.0𝐢 + 3.4𝐣 + 0.0𝐤
```
