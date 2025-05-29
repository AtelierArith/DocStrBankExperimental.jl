```
@multilinear f
@multilinear f f0
```

This macro defines a multilinear extension of the function `f` (or `f0`). This is analogous to `@linear f`. The new methods accepts both terms and linear combinations as arguments. It linearly expands all arguments that are linear combinations and then calls `f` for each combination of terms. If `f0` is specified, then `f0` is called instead to evaluate terms.

The new method always returns a linear combination (of type `Linear` unless this is overriden by the `addto` keyword). The term type is inferred from the return type of `f` (or `f0`) with terms as arguments. The coefficient type is computed by promoting the coefficient types of all `AbstractLinear` arguments. In case `f` (or `f0`) returns a linear combination for term arguments, that coefficient type is also taken into account.

In order to catch all possible combinations of terms and linear combinations, `@multilinear f` and `@multilinear f f0` define a single new method `f(x...; kw...)` that matches **all** argument types. (This is different from `@linear`.) Hence, if `f0` is not given, then the methods for `f` that evaluate terms must have a non-generic signature. If instead the signature also is `f(x::Any...)`, then this method is overwritten, resulting in an error when `f` is called.

The new method defined by `@multilinear` accepts all keyword arguments discussed for `@linear`. Unknown keyword arguments are passed on to the call for term evaluation. The macro `@linear_kw` works as for linear functions.

If the two-argument version of `@multilinear` is used, then typically there is no other method for `f`. Hence `f` returns a linear combination for all arguments in this case. If all arguments are terms and also `f0` returns a term, then the coefficient type is `LinearCombinations.DefaultCoefftype`. For the one-argument version there must be at least one other method as discussed above. So `f` may not return a linear combination for all arguments.

See also [`@linear`](@ref), [`@linear_kw`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# Examples

## Bilinear extension of a function returning a term

```jldoctest multilinear
julia> f(x::Char, y::String) = x*y; @multilinear f

julia> a, b = Linear('x' => 1, 'y' => 2), Linear("z" => 1.0, "w" => -1.0)
(Linear{Char, Int64}('x' => 1, 'y' => 2), Linear{String, Float64}("w" => -1.0, "z" => 1.0))

julia> f(a, "z")
Linear{String, Int64} with 2 terms:
2*"yz"+"xz"

julia> f('x', b)
Linear{String, Float64} with 2 terms:
-"xw"+"xz"

julia> f(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"
```

## Bilinear extension of a function returning a linear combination

```jldoctest multilinear
julia> f(x::Char, y::String) = Linear(x*y => BigInt(1), y*x => BigInt(-1)); @multilinear f

julia> f(a, b)   # same a and b as before
Linear{String, BigFloat} with 8 terms:
-2.0*"zy"-"xw"-"zx"+2.0*"yz"+"wx"-2.0*"yw"+"xz"+2.0*"wy"

julia> typeof(ans)
Linear{String, BigFloat}
```

## Multilinear extension of a function

```jldoctest multilinear
julia> g(xs::Union{Char,String}...) = *(xs...); @multilinear g

julia> g(a)   # same a and b as before
Linear{String, Int64} with 2 terms:
"x"+2*"y"

julia> g(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"

julia> g(a, b, a)
Linear{String, Float64} with 8 terms:
-"xwx"+"xzx"+4.0*"yzy"+2.0*"xzy"+2.0*"yzx"-2.0*"ywx"-2.0*"xwy"-4.0*"ywy"
```

## Multilinear extension using the two-argument version of `@multilinear`

```jldoctest multilinear
julia> @multilinear(h, *)

julia> h(a, b; coeff = 2)   # same a and b as before
Linear{String, Float64} with 4 terms:
-2.0*"xw"+4.0*"yz"-4.0*"yw"+2.0*"xz"
```
