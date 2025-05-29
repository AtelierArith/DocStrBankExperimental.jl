This   package  introduces  finite  fields   using  the  GAP  syntax.  This compatibility   with  GAP  is  the  motivation  not  to  use  the  existing `GaloisFields`.  The  speed  is  comparable  with  `GaloisFields`, slightly slower  for prime fields and faster for composite fields. Lke GAP3, we only implement  fields  of  order  less  than  2^16. This package comes with the module  `Modulo` implementing modular arithmetic without restriction on the modulus (the modulus can be a `BigInt`).

This only dependency of this package is `Primes`.

The Galois field with `p^n` elements is obtained as `GF(p^n)`. All elements of  Galois fields of characteristic `p`  have the same type, the parametric type   `FFE{p}`.  The  function   `Z(p^n)`  returns  a   generator  of  the multiplicative group of `GF(p^n)`. Other elements of `GF(p^n)` are obtained as  powers of `Z(p^n)`, except `0`, obtained as `0*Z(p^n)`. Elements of the prime  field can  also be  obtained as  `FFE{p}(n)` (which  is the  same as `n*Z(p)^0`).

```julia-repl
julia> a=Z(64)
FFE{2}: Z₆₄

julia> a^9 # automatic conversion to smaller fields
FFE{2}: Z₈

julia> a^21
FFE{2}: Z₄

julia> a+1
FFE{2}: Z₆₄⁵⁶
```

Elements  of the prime field can be converted to `Mod(,p)` or to integers:

```julia-repl
julia> a=Z(19)+3
FFE{19}: 5

julia> Mod(a)
Mod{UInt64}: 5₁₉

julia> Int(a)
5

julia> order(a) # order as element of the multiplicative group
9
```

The field, `p`, `n` and `p^n` can be obtained back from an `FFE{p}` as well as which power of `Z(p^n)` is considered

```julia-repl
julia> a=Z(8)^5
FFE{2}: Z₈⁵

julia> F=field(a)
GF(2^3)

julia> char(F)
2

julia> char(a)
2

julia> degree(F)
3

julia> degree(a)
3

julia> length(F)
8

julia> log(a)
5

julia> elements(F)
8-element Vector{FFE{2}}:
   0
   1
  Z₈
 Z₈²
 Z₈³
 Z₈⁴
 Z₈⁵
 Z₈⁶
```

A  `p`-integral integer or  rational or a  `Mod(,p)` can be  converted to a prime field element using `FFE{p}` as a constructor.

```julia-repl
julia> FFE{19}(2)
FFE{19}: 2

julia> FFE{19}(5//3)
FFE{19}: 8

julia> FFE{19}(Mod(2,19))
FFE{19}: 2
```

```julia-rep1
julia> m=rand(GF(49),4,4)
4×4 Matrix{FFE{7}}:
 Z₄₉²⁴  Z₄₉¹⁸   Z₄₉⁹  Z₄₉⁴²
 Z₄₉²²  Z₄₉⁴¹  Z₄₉⁴⁶  Z₄₉²⁴
 Z₄₉¹⁵  Z₄₉¹⁹  Z₄₉⁴⁰   Z₄₉³
 Z₄₉²⁰  Z₄₉²⁹  Z₄₉³⁶  Z₄₉²⁰

julia> inv(m)
4×4 Matrix{FFE{7}}:
 Z₄₉³⁷   Z₄₉⁵  Z₄₉³⁶      1
 Z₄₉¹⁰    Z₄₉   Z₄₉⁶  Z₄₉⁴⁷
 Z₄₉³⁰  Z₄₉³⁸    Z₄₉     -2
 Z₄₉¹⁵   Z₄₉²      1  Z₄₉²⁸

julia> inv(m)*m
4×4 Matrix{FFE{7}}:
 1  0  0  0
 0  1  0  0
 0  0  1  0
 0  0  0  1
```
