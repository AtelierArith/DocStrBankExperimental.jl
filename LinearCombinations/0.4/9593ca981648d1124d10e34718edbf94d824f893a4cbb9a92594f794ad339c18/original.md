```
(tf::AbstractTensor)(tx::AbstractTensor...) -> Tensor
```

Evaluating an `AbstractTensor` on other `AbstractTensor`s (with the same number of components) is done componentwise. If the degrees of the components and the maps are not all zero, then the usual sign is introduced: whenever a map `f` is moved past a component `x`, then this changes the sign by `(-1)^(deg(f)*deg(x))`.

# Examples

## Examples without degrees

```jldoctest tensorcall
julia> @linear f; f(x) = uppercase(x)
f (generic function with 2 methods)

julia> @linear g; g(x) = lowercase(x)
g (generic function with 2 methods)

julia> const h = Tensor(f, g)
f⊗g

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear('Z' => -1, 'W' => 3)
Linear{Char, Int64} with 2 terms:
-'Z'+3*'W'

julia> h(Tensor('x', 'Z'))
Linear{Tensor{Tuple{Char, Char}}, Int64} with 1 term:
'X'⊗'z'

julia> h(tensor(a, b))
Linear{Tensor{Tuple{Char, Char}}, Int64} with 4 terms:
6*'Y'⊗'w'-2*'Y'⊗'z'+3*'X'⊗'w'-'X'⊗'z'
```

## Examples with degrees

We again take the length of a `String` as its degree.

```jldoctest tensorcall
julia> import LinearCombinations: deg

julia> deg(x::String) = length(x);

julia> struct P{T} y::T end; deg(p::P) = deg(p.y);

julia> @linear p::P; (p::P)(x) = x * p.y

julia> p = P("pp"); q = P("qqq")
P{String}("qqq")

julia> j = Tensor(p, q)
P{String}("pp")⊗P{String}("qqq")

julia> j(Tensor("x", "yy"))
Linear{Tensor{Tuple{String, String}}, Int64} with 1 term:
-"xpp"⊗"yyqqq"

julia> a = Linear("x" => 1, "yy" => 2)
Linear{String, Int64} with 2 terms:
"x"+2*"yy"

julia> b = tensor(a, a)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
2*"yy"⊗"x"+"x"⊗"x"+4*"yy"⊗"yy"+2*"x"⊗"yy"

julia> j(b)
Linear{Tensor{Tuple{String, String}}, Int64} with 4 terms:
4*"yypp"⊗"yyqqq"+2*"yypp"⊗"xqqq"-2*"xpp"⊗"yyqqq"-"xpp"⊗"xqqq"
```

## A multilinear example

```jldoctest
julia> @multilinear f; f(x::Char...) = join(x, '#');

julia> @multilinear g; g(x::Char...) = join(x, '@');

julia> f('a', 'p', 'x')
"a#p#x"

julia> Tensor(f, g)(Tensor('a', 'b'), Tensor('p', 'q'), Tensor('x', 'y'))
Linear{Tensor{Tuple{String, String}}, Int64} with 1 term:
"a#p#x"⊗"b@q@y"
```
