```
lc1, mvf1, lc2, mvf2 = example_moebius(p)
```

Create two simplicial complexes for a cylinder and Moebius strip, respectively, together with associated multivector fields on them.

The function returns the Lefschetz complexes `lc1` and `lc2`, as well as the multivector fields `mvf1` and `mvf2`. Both complexes are over a field with characteristic `p`. Positive  prime characteristic uses the finite field GF(p), while zero characteristic gives the rationals.

The multivector field is the same, and it has one critical  cell each in dimension 1 and 2 in the interior of the strip. The boundary consists of two periodic orbits for `lc1` and `mvf1`, and of one periodic orbit in the Moebius case `lc2` and `mvf2`. The latter case leads to different connection matrices for the fields GF(2) and GF(7), for example.

# Examples

```jldoctest
julia> lc1, mvf1, lc2, mvf2 = example_moebius(0);

julia> lc2p2 = lefschetz_gfp_conversion(lc2,2);

julia> lc2p7 = lefschetz_gfp_conversion(lc2,7);

julia> cmp2 = connection_matrix(lc2p2, mvf2);

julia> cmp7 = connection_matrix(lc2p7, mvf2);

julia> sparse_show(cmp2.matrix)
[0   0   0   0]
[0   0   0   1]
[0   0   0   0]
[0   0   0   0]

julia> sparse_show(cmp7.matrix)
[0   0   0   0]
[0   0   0   1]
[0   0   0   2]
[0   0   0   0]
```
