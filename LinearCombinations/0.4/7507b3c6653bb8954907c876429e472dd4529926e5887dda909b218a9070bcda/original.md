```
@linear f
```

This macro defines a linear extension of the function (or callable object) `f`. More specifically, it defines a new method `f(a::AbstractLinear{T,R}; kw...) where {T,R}` that returns the linear combination obtained by summing up `c*f(x)` for all term-coefficient pairs `x => c` appearing in `a`.

The new method recognizes the following keyword arguments:

  * `coefftype`:   This optional keyword argument specifies the coefficient type of the linear combination returned   by `f(a)` if the keyword argument `addto` is not present. If `coefftype` is also not specified   and `f(x::T)` is a term (as opposed to a linear combination), then `coefftype` is set to `R`.   If `f(x::T) <: AbstractLinear`, say with coefficient type `S`, then `promote_type(R, S)`   is chosen as the new coefficient type. If the `addto` keyword is present, then `coefftype` is ignored.

    Because of the way Julia handles keyword arguments, the form `f(a; coefftype = Int)` is not type-stable.   Type stability can be achieved by saying `f(a; coefftype = Val(Int))`.
  * `addto::AbstractLinear`:   If given, the sum of all terms `c*f(x)` is added to `addto`, and the result is returned.   This avoids allocating a new linear combination each time `f` is called with an `AbstractLinear` argument.   The default value for `addto` is `Linear{U,coefftype}`. Here `U` is the return type of `f(x::T)`   if this return type is not a subtype of `AbstractLinear` and the term type of the return values otherwise.
  * `coeff`:   This optional keyword argument allows to efficiently compute scalar multiples of `f(a)`. More precisely,   `f(a; coeff = c)` returns `c*f(a)`, and `f(a; addto = b, coeff = c)` adds `c*f(a)` to `b` and returns   this new value.
  * `sizehint::Bool = true`:   The new method for `f` may call `sizehint!` for `addto` to pre-allocate room for the new terms.   This keyword argument permits to turn pre-allocation off.

All other keyword arguments are passed on to `f(x)`. With the macro `@linear_kw` one can make `f(a)` pass the special keyword arguments listed above on to `f(x)`, too.

See also [`@multilinear`](@ref), [`sizehint!`](@ref), [`@linear_kw`](@ref), [`keeps_filtered`](@ref).

# Examples

## Linear extension of a function returning a term

```jldoctest linear
julia> f(x) = uppercase(x); @linear f
f (generic function with 2 methods)

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> f(a)
Linear{Char, Int64} with 2 terms:
2*'Y'+'X'

julia> f(a; coefftype = Float64)
Linear{Char, Float64} with 2 terms:
2.0*'Y'+'X'

julia> b = Linear('z' => 3); f(a; addto = b, coeff = -1); b
Linear{Char, Int64} with 3 terms:
-2*'Y'-'X'+3*'z'
```

## Linear extension of a function returning a linear combination

```jldoctest linear
julia> g(x) = Linear(x*x => 1.0, string(x) => -1.0); @linear g
g (generic function with 2 methods)

julia> g("x"), g("")
(Linear{String, Float64}("xx" => 1.0, "x" => -1.0), Linear{String, Float64}())

julia> g(a)   # same a as before
Linear{String, Float64} with 4 terms:
"xx"-"x"+2.0*"yy"-2.0*"y"

julia> g(a; coefftype = Val(Int), coeff = 3.0)
Linear{String, Int64} with 4 terms:
3*"xx"-3*"x"+6*"yy"-6*"y"
```

## Linear extension of a callable object

```jldoctest linear
julia> struct P y::String end

julia> (p::P)(x) = p.y*x*p.y; @linear p::P

julia> p = P("w"); p(a)   # same a as before
Linear{String, Int64} with 2 terms:
"wxw"+2*"wyw"
```
