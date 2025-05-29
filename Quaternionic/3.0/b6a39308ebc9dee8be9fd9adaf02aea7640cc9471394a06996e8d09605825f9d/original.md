```
imx
𝐢
```

The quaternionic unit associated with rotation about the `x` axis.  Can also be entered as Unicode bold `𝐢` (which can be input as `\bfi<tab>`).

Note that — just as `im` is a `Complex{Bool}` — `imx` is a `QuatVec{Bool}`, and as soon as you multiply by a scalar of any other number type (e.g., a `Float64`) it will be promoted to a `QuatVec` of that number type, and once you *add* a scalar it will be promoted to a `Quaternion`.

See also [`imy`](@ref) and [`imz`](@ref).

# Examples

```jldoctest
julia> imx * imx
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imx
 + 1.2𝐢 + 0.0𝐣 + 0.0𝐤
julia> 1.2 + 3.4imx
1.2 + 3.4𝐢 + 0.0𝐣 + 0.0𝐤
julia> 1.2 + 3.4𝐢
1.2 + 3.4𝐢 + 0.0𝐣 + 0.0𝐤
```
