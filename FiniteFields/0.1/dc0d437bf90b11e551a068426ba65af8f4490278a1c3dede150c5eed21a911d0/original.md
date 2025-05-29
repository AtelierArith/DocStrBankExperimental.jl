`Z(p^d)`

returns  a  generator  of  the  multiplicative  group  of  the finite field `𝔽_{pᵈ}`,  where    `p`  must  be  prime  and `pᵈ` smaller than `2¹⁵`. This multiplicative  group  is  cyclic  thus  `Z(pᵈ)ᵃ`  runs  over it for `a` in `0:pᵈ-1`.  The zero  of the  field is  `0*Z(p)` (the  same as `0*Z(pᵈ)`; we automatically lower an element to the smallest field which contains it).

The  various generators returned by `Z` for finite fields of characteristic `p`  are compatible. That  is, if the  field `𝔽_{pⁿ}` is  a subfield of the field `𝔽_{pᵐ}`, that is, `n` divides `m`, then `Z(pⁿ)=Z(pᵐ)^div(pᵐ-1,pⁿ-1)`.  This is  achieved by  choosing `Z(p)` as the smallest  primitive root  modulo `p`  and `Z(pⁿ)`  as a  root of the `n`-th Conway polynomial of characteristic `p`. Those polynomials where defined by J.H.~Conway and computed by R.A.~Parker.

```julia-repl
julia> z=Z(16)
FFE{2}: Z₁₆

julia> z^5
FFE{2}: Z₄
```
