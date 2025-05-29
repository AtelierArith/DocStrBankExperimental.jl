```
imz
𝐤
```

The quaternionic unit associated with rotation about the `z` axis.  Can also be entered as Unicode bold `𝐤` (which can be input as `\bfk<tab>`).

Note that — just as `im` is a `Complex{Bool}` — `imz` is a `QuatVec{Bool}`, and as soon as you multiply by a scalar of any other number type (e.g., a `Float64`) it will be promoted to a `QuatVec` of that number type, and once you *add* a scalar it will be promoted to a `Quaternion`.

See also [`imx`](@ref) and [`imy`](@ref).

# Examples

```jldoctest
julia> imz * imz
-1 + 0𝐢 + 0𝐣 + 0𝐤
julia> 1.2imz
 + 0.0𝐢 + 0.0𝐣 + 1.2𝐤
julia> 1.2 + 3.4imz
1.2 + 0.0𝐢 + 0.0𝐣 + 3.4𝐤
julia> 1.2 + 3.4𝐤
1.2 + 0.0𝐢 + 0.0𝐣 + 3.4𝐤
```
