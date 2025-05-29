```
TensorSplat(f)
```

`TensorSplat` turns a multilinear function `f` into a linear function acting on terms of type `Tensor`. This is similar to [splatting](https://docs.julialang.org/en/v1/manual/faq/#...-splits-one-argument-into-many-different-arguments-in-function-calls) in Julia.

When called with an argument of type `Tensor`, the new function returns the the value of `f` on the components of the tensor (which may or may not be a linear combination). All keyword arguments are passed on to `f` in this case.

When called with a linear combination as argument, the new function returns a linear combination. It recognizes all keyword arguments discussed for `@linear`. Unknown keyword arguments are passed on to `f`.

See also [`Tensor`](@ref), [`tensor`](@ref), [`TensorSlurp`](@ref), [`@linear`](@ref).

# Examples

```jldoctest
julia> const f = MultilinearExtension(*)
MultilinearExtension(*)

julia> const g = TensorSplat(f)
TensorSplat(MultilinearExtension(*))

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear("w" => 3, "z" => -1)
Linear{String, Int64} with 2 terms:
3*"w"-"z"

julia> f(a, b)
Linear{String, Int64} with 4 terms:
3*"xw"-2*"yz"+6*"yw"-"xz"

julia> c = tensor(a, b)
Linear{Tensor{Tuple{Char, String}}, Int64} with 4 terms:
3*'x'⊗"w"-'x'⊗"z"-2*'y'⊗"z"+6*'y'⊗"w"

julia> g(c)
Linear{String, Int64} with 4 terms:
3*"xw"-2*"yz"+6*"yw"-"xz"

julia> g(c; addto = f(a, b), coeff = -1)
Linear{String, Int64} with 0 terms:
0
```
