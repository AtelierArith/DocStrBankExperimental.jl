```
coprod(t::T) where T <: AbstractTensor -> Linear{Tensor{Tuple{T,T}}}
```

Return the coproduct of a tensor, computed from the coproducts of its components. Signs are introduced according to the usual sign rule. If all degrees are integers, then the coefficient type is `DefaultCoefftype`.

This function is linear.

See also: [`coprod`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# Example

```jldoctest
julia> import LinearCombinations: deg, coprod

julia> deg(x::String) = length(x);

julia> coprod(x::String) = Linear(Tensor(x[1:k], x[k+1:end]) => 1 for k in 1:length(x)-1);

julia> coprod("abc")
Linear{Tensor{Tuple{String, String}}, Int64} with 2 terms:
"a"⊗"bc"+"ab"⊗"c"

julia> t = Tensor("abc", "xyz")
"abc"⊗"xyz"

julia> coprod(t)
Linear{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 4 terms:
("a"⊗"xy")⊗("bc"⊗"z")-("ab"⊗"x")⊗("c"⊗"yz")+("a"⊗"x")⊗("bc"⊗"yz")+("ab"⊗"xy")⊗("c"⊗"z")
```
