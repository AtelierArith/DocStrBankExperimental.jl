```
swap(t::AbstractTensor{Tuple{T1,T2}}) where {T1,T2} -> AbstractLinear{Tensor{Tuple{T2,T1}}}
swap(a::AbstractLinear{AbstractTensor{Tuple{T1,T2}})}) where {T1,T2}
    -> AbstractLinear{Tensor{Tuple{T1,T2}})}
```

This linear function swaps the components of two-component tensors. If the two components of a tensor `t` have non-zero degrees, then the usual sign `(-1)^(deg(t[1])*deg(t[2]))` is introduced. By default, all terms have zero degree.

Note that `swap` is a special case of `regroup`:  it is simply defined as `regroup(:((1, 2)), :((2, 1)))`.

See also [`Tensor`](@ref), [`deg`](@ref), [`regroup`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# Examples

## Examples without degrees

```jldoctest swap
julia> t = Tensor("x", "z")
"x"⊗"z"

julia> swap(t)
Linear1{Tensor{Tuple{String, String}}, Int64} with 1 term:
"z"⊗"x"

julia> a = Linear("x" => 1, "yy" => 1) ⊗ Linear("z" => 1, "ww" => 1)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"x"⊗"ww"+"yy"⊗"ww"+"yy"⊗"z"+"x"⊗"z"

julia> swap(a)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"ww"⊗"x"+"z"⊗"yy"+"z"⊗"x"+"ww"⊗"yy"

julia> swap(a; coeff = 2)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
2*"ww"⊗"x"+2*"z"⊗"yy"+2*"z"⊗"x"+2*"ww"⊗"yy"
```

## Examples with degrees

For simplicity, we define the degree of a `String` to be its length.

```jldoctest swap
julia> LinearCombinations.deg(x::String) = length(x)

julia> swap(t)   # same t as before
Linear1{Tensor{Tuple{String, String}}, Int64} with 1 term:
-"z"⊗"x"

julia> swap(a)   # same a as before
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
"ww"⊗"x"+"z"⊗"yy"-"z"⊗"x"+"ww"⊗"yy"
```
