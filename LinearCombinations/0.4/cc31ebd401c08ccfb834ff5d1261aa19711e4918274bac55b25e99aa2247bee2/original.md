```
diff(t::T) where T <: AbstractTensor -> Linear{T}
```

Return the differential of the tensor `t` by differentiating each tensor factor at a time and adding signs according to the degrees of the components. The coefficient type is usually `DefaultCoefftype`. However, if the degrees of the tensor components are not integers, then the coefficient type is chosen such that it can accommodate the signs.

See also [`diff`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# Example

As usual, the degree of a string is its length.

```jldoctest
julia> import LinearCombinations: deg, diff

julia> deg(x::String) = length(x);

julia> function diff(x::String)
           if isempty(x) || x[1] == 'D'
               zero(Linear1{String,Int})
           else
               Linear1('D'*x => 1)end
       end;

julia> dx = diff("x")
Linear1{String, Int64} with 1 term:
"Dx"

julia> diff(dx)
Linear1{String, Int64} with 0 terms:
0

julia> t = Tensor("a", "bb", "ccc")
"a"⊗"bb"⊗"ccc"

julia> diff(t)
Linear{Tensor{Tuple{String, String, String}}, Int64} with 3 terms:
-"a"⊗"bb"⊗"Dccc"-"a"⊗"Dbb"⊗"ccc"+"Da"⊗"bb"⊗"ccc"
```
