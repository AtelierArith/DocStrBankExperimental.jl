```
integer_genera(sig_pair::Vector{Int}, determinant::RationalUnion;
       min_scale::RationalUnion = min(one(QQ), QQ(abs(determinant))),
       max_scale::RationalUnion = max(one(QQ), QQ(abs(determinant))),
       even=false)                                         -> Vector{ZZGenus}
```

Return a list of all genera with the given conditions. Genera of non-integral $\mathbb Z$-lattices are also supported.

# Arguments

  * `sig_pair`: a pair of non-negative integers giving the signature
  * `determinant`: a rational number; the sign is ignored
  * `min_scale`: a rational number; return only genera whose scale is an integer multiple of `min_scale` (default: `min(one(QQ), QQ(abs(determinant)))`)
  * `max_scale`: a rational number; return only genera such that `max_scale` is an integer multiple of the scale (default: `max(one(QQ), QQ(abs(determinant)))`)
  * `even`: boolean; if set to true, return only the even genera (default: `false`)
