```
@linear_kw function def
```

`@linear_kw` scans a function definition for the keywords `coefftype`, `addto`, `coeff` and `sizehint` and makes them known to the `LinearCombinations` package. This allows to write performant code. Not all keywords have to present. However, `addto` and `coeff` only have an effect if used together.

See also [`LinearCombinations.has_coefftype`](@ref), [`LinearCombinations.has_addto_coeff`](@ref), [`LinearCombinations.has_isfiltered`](@ref), [`LinearCombinations.has_sizehint`](@ref), [`LinearCombinations.unval`](@ref).

# Example

Consider the following two functions:

```jldoctest addto-coeff; output = false
f(x::Char) = Linear(uppercase(x) => 1, x => -1)

@linear f

using LinearCombinations: unval   # unwraps a Val argument

@linear_kw function g(x::Char;
        coefftype = Int,
        addto = zero(Linear{Char,unval(coefftype)}),
        coeff = 1)
    addmul!(addto, uppercase(x), coeff)
    addmul!(addto, x, -coeff)
    addto
end

@linear g

# output

g (generic function with 2 methods)
```

The linear extensions are functionally equivalent,  but `g` will be much faster than `f`.

```jldoctest addto-coeff
julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> f(a; coefftype = Float64, coeff = 2)
Linear{Char, Float64} with 4 terms:
4.0*'Y'-2.0*'x'-4.0*'y'+2.0*'X'

julia> g(a; coefftype = Float64, coeff = 2)
Linear{Char, Float64} with 4 terms:
4.0*'Y'-2.0*'x'-4.0*'y'+2.0*'X'
```

Test whether keywords have been registered:

```jldoctest addto-coeff
julia> using LinearCombinations: has_coefftype, has_addto_coeff, has_sizehint

julia> has_coefftype(g, Char), has_addto_coeff(g, Char), has_sizehint(g, Char)
(true, true, false)
```
