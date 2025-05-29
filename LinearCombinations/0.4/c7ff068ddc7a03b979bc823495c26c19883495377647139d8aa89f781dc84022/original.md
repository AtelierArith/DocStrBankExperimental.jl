```
MultilinearExtension(f)
MultilinearExtension(f, name)
```

An element of this type is a multilinear extension of `f`. One can additionally specify the name displayed for it.

# Example

```jldoctest
julia> a, b = Linear('x' => 1, 'y' => 2), Linear("z" => 1.0, "w" => -1.0)
(Linear{Char, Int64}('x' => 1, 'y' => 2), Linear{String, Float64}("w" => -1.0, "z" => 1.0))

julia> const concat = MultilinearExtension(*, "concat")
concat

julia> concat(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"
```
