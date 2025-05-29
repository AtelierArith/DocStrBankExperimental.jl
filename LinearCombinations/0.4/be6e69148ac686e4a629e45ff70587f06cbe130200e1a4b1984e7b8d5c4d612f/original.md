```
L(xc::Pair...; is_filtered = false; kw...) where L <: AbstractLinear
L(itr; is_filtered = false; kw...) where L <: AbstractLinear
```

`AbstractLinear{T,R}` is the supertype of all linear combinations with term type `T` and coefficient type `R`.

A constructor for a subtype `L <: AbstractLinear` constructs a linear combination of type `L` out of the given term-coefficient pairs of the form `x => c` where `x` is the term and `c` the coefficient, or out of the pairs provided by the iterator `itr`. It must be possible to convert all terms and coefficients to the chosen term type and coefficient type, respectively.

Neither the term type nor the coefficient type need to be concrete. (Of course, concrete types lead to better performance.) If the coefficient type and possibly also the term type are not specified, the constructor tries to determine them using `promote_type` (for coefficients) and `promote_typejoin` (for terms).

If two or more term-coefficient pairs are given with the same term, then the corresponding coefficients are added up. This is different from dictionaries, where any key-value pair overrides previous pairs with the same key. However, the implemented behavior is more useful for linear combinations.

For specialized applications, terms and coefficients can be processed with `linear_filter` and `termcoeff` before being stored in a linear combination. The keyword argument `is_filtered` controls whether `linear_filter` is called for each term.

By default, linear combinations are displayed in a human-readable form with a limited number of terms. Dedicated `show` methods display all terms of a linear combination or return an expression that Julia can parse as input. See the examples below.

See also [`Linear`](@ref), [`DenseLinear`](@ref), [`Linear1`](@ref), [`linear_filter`](@ref), [`LinearCombinations.termcoeff`](@ref), `Base.show`

# Examples

```jldoctest abstractlinear
julia> Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> Linear(x => c for (c, x) in enumerate('u':'z'))
Linear{Char, Int64} with 6 terms:
3*'w'+2*'v'+4*'x'+'u'+5*'y'+6*'z'

julia> Linear{Char,Int}('x' => 1, 'y' => Int8(0), 'x' => 3.0)
Linear{Char, Int64} with 1 term:
4*'x'

julia> a = Linear('x' => BigInt(1), "yz" => 2.0)
Linear{Any, BigFloat} with 2 terms:
'x'+2.0*"yz"
```

Iterating over a linear combination yields all non-zero term-coefficient pairs. Hence a linear combination can itself be used an argument to an `AbstractLinear` constructor.

```jldoctest abstractlinear
julia> Linear{Union{Char,String}}(a)   # same a as before
Linear{Union{Char, String}, BigFloat} with 2 terms:
'x'+2.0*"yz"
```

Various forms to display a linear combination.

```jldoctest
julia> a = Linear(x => 1 for x in 'a':'z')
Linear{Char, Int64} with 26 terms:
'n'+'f'+'w'+'d'+'e'+'o'+'h'+'j'+'i'+'k'+'r'+'s'+'t'+'q'+'y'+'a'+'c'+'p'+'m'+'z'±⋯

julia> show(stdout, MIME"text/plain"(), a)  # all terms
Linear{Char, Int64} with 26 terms:
'n'+'f'+'w'+'d'+'e'+'o'+'h'+'j'+'i'+'k'+'r'+'s'+'t'+'q'+'y'+'a'+'c'+'p'+'m'+'z'+'g'+'v'+'l'+'u'+'x'+'b'

julia> b = Linear('a' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'a'+2*'y'

julia> show(b)  # can be parsed as input
Linear{Char, Int64}('a' => 1, 'y' => 2)
```
