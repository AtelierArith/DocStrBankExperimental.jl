```
tensor(xs...) -> Linear{Tensor}
x1 ⊗ x2 ⊗ ... -> Linear{Tensor}
```

`tensor` is the multilinear extension of `Tensor`. `⊗` is a synomym for `tensor`. Note that `tensor` always returns a linear combination.

See also [`Tensor`](@ref), [`@multilinear`](@ref)

# Examples

```jldoctest
julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear("w" => 3, "z" => -1)
Linear{String, Int64} with 2 terms:
3*"w"-"z"

julia> tensor(a, "w")
Linear{Tensor{Tuple{Char, String}}, Int64} with 2 terms:
'x'⊗"w"+2*'y'⊗"w"

julia> tensor(a, b)
Linear{Tensor{Tuple{Char, String}}, Int64} with 4 terms:
3*'x'⊗"w"-'x'⊗"z"-2*'y'⊗"z"+6*'y'⊗"w"

julia> tensor('x', b, a; coefftype = Float64)
Linear{Tensor{Tuple{Char, String, Char}}, Float64} with 4 terms:
6.0*'x'⊗"w"⊗'y'+3.0*'x'⊗"w"⊗'x'-2.0*'x'⊗"z"⊗'y'-'x'⊗"z"⊗'x'

julia> a = tensor(); a[Tensor()]
1
```
