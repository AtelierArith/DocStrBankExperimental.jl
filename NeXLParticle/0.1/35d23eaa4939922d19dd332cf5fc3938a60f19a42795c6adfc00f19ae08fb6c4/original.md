```
signature( #
    sig::Signature,
    krs::Vector{KRatio},
    special::Set{Element},
    drop::Set{Element}
)::Dict{Element,Float64}
```

Computes a "particle signature" from the specified set of k-ratios.  A particle signature is similar to normalized k-ratios relative to pure elements except 1) certain elements can be removed from the normalization; and 2) these elements can be include in the result as un-normalized.
