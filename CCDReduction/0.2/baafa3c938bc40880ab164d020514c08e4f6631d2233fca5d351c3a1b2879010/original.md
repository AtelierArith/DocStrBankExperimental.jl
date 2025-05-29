```
CCDData <: AbstractCCDData
CCDData(data::AbstractMatrix, [hdr::FITSHeader])
```

Struct to store `ImageHDU`, derived from [`AbstractCCDData`](@ref).

`CCDData` acts like a matrix with a header associated.

```julia
ccd = CCDData(zeros(4, 4))

ccd[1]
```

This accesses the 1st element in matrix associated with `ccd`.

```julia
ccd["SIMPLE"]
```

One can also access the header directly from `ccd`, the key can be `Symbol` as well.

```julia
ccd[:SIMPLE] = false
```

Header values can be directly modified from `ccd`.

One can perform arithmetic operations on it as well:

```julia
ccd1 = CCDData(zeros(4, 4))
ccd2 = CCDData(ones(4, 4))
sum_ccd1 = ccd1 + ccd2
sum_ccd2 = ccd2 + ccd1
```

`sum_ccd1` has the header of `ccd1` whereas `sum_ccd2` has the header `ccd2`.

If header is not provided in the `CCDData` constructor, `default_header` is used to generate the header.
