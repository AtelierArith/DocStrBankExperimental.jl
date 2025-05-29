```
LinearCombinations.linear_filter(x) -> Bool
```

Return `true` if the term `x` is to be stored in linear combinations and `false` if it is to be dropped.

The effect of this is that linear combinations don't live in the vector space (or free module) spanned by all possible terms, but rather in the quotient by the subspace (or submodule) spanned by the terms for which `linear_filter` returns `false`. Setting coefficients for terms that are divided out is allowed, but has no effect.

The default return value of `linear_fiilter` is `true` for all arguments, so that nothing is divided out.

See also [`keeps_filtered`](@ref), [`LinearCombinations.termcoeff`](@ref).

# Example

```julia-repl
julia> LinearCombinations.linear_filter(x::Char) = islowercase(x)

julia> a = Linear('x' => 1, 'Y' => 2)
x

julia> a['Z'] = 3
3

julia> a
x
```
