```
TensorSlurp(f)
```

`TensorSlurp` turns a linear function acting on `Tensor` terms into a multilinear function. This is similar to [slurping](https://docs.julialang.org/en/v1/manual/faq/#...-combines-many-arguments-into-one-argument-in-function-definitions) in Julia.

The new function always returns a linear combination, even if none of the arguments is a linear combination. It recognizes all keyword arguments discussed for `@linear`. Unknown keyword arguments are passed on to `f`.

See also [`Tensor`](@ref), [`tensor`](@ref), [`TensorSplat`](@ref), [`@linear`](@ref).

# Examples

We use [`swap`](@ref) as an example of a function acting on tensors.

```jldoctest
julia> const f = TensorSlurp(swap)
TensorSlurp(Regroup{(1, 2),(2, 1)})

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear("w" => 3, "z" => -1)
Linear{String, Int64} with 2 terms:
3*"w"-"z"

julia> c = tensor(a, b)
Linear{Tensor{Tuple{Char, String}}, Int64} with 4 terms:
3*'x'⊗"w"-'x'⊗"z"-2*'y'⊗"z"+6*'y'⊗"w"

julia> swap(c)
Linear{Tensor{Tuple{String, Char}}, Int64} with 4 terms:
-"z"⊗'x'-2*"z"⊗'y'+6*"w"⊗'y'+3*"w"⊗'x'

julia> f(a, b)
Linear{Tensor{Tuple{String, Char}}, Int64} with 4 terms:
-"z"⊗'x'-2*"z"⊗'y'+6*"w"⊗'y'+3*"w"⊗'x'

julia> f(a, b; addto = swap(c), coeff = -1)
Linear{Tensor{Tuple{String, Char}}, Int64} with 0 terms:
0
```
