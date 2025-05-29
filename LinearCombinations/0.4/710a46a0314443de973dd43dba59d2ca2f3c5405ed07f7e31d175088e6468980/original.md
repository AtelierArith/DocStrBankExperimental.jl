```
Tensor{T<:Tuple}

Tensor{T}(xs...) where T
Tensor(xs...)
```

The type `Tensor` represents pure tensors.

A general tensor is a linear combination of pure tensors and can conveniently be created using `tensor`. `LinearCombinations` takes pure tensors as basis elements.

A `Tensor` can be created out of a `Tuple` or out of the individual components. The second form is not available if the tensor has a tuple as its only component.

`Tensor` implements the [iteration](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) and [indexing](https://docs.julialang.org/en/v1/manual/interfaces/#Indexing) interfaces. This makes for example splatting available for tensors, and the `i`-th component of `t::Tensor` can be accessed as `t[i]`.

Tensors can be nested. Different bracketings lead to different tensors. The functions `cat`, `flatten`, `swap` and `regroup` are provided to make rearranging tensors more easily.

Note that the type parameter of `Tensor` is always a `Tuple`. For instance, the type of a `Tensor` with two components of types `T1` and `T2` is `Tensor{Tuple{T1,T2}}`, not `Tensor{T1,T2}`.

See also [`tensor`](@ref), [`cat`](@ref), [`flatten`](@ref), [`regroup`](@ref), [`swap`](@ref).

# Examples

```jldoctest
julia> t = Tensor('x', 'y', "z")
'x'⊗'y'⊗"z"

julia> typeof(t)
Tensor{Tuple{Char, Char, String}}

julia> Tuple(t)
('x', 'y', "z")

julia> length(t), t[2], t[end]
(3, 'y', "z")

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear(Tensor('x', 'z') => 1, Tensor('y', 'z') => 2)
Linear{Tensor{Tuple{Char, Char}}, Int64} with 2 terms:
2*'y'⊗'z'+'x'⊗'z'

julia> b == tensor(a, 'z')
true

julia> [uppercase(x) for x in t]
3-element Vector{Any}:
 'X': ASCII/Unicode U+0058 (category Lu: Letter, uppercase)
 'Y': ASCII/Unicode U+0059 (category Lu: Letter, uppercase)
 "Z"

julia> f((x1, xs...)::Tensor) = x1
f (generic function with 1 method)

julia> f(t)
'x': ASCII/Unicode U+0078 (category Ll: Letter, lowercase)

julia> t == Tensor(Tensor('x', 'y'), "z")
false

julia> a = tensor(); a[Tensor()]
1
```
