```
BiweightTransform(X; c=9, M=nothing)
```

Creates an iterator based on the biweight transform.[^1] This iterator will first filter all input data so that only finite values remain. Then, the iteration will progress using a custom state, which includes a flag to indicate whether the value is within the cutoff, which is `c` times the median-absolute-deviation (MAD). The MAD is based on the deviation from `M`, which will default to the median of `X` if `M` is `nothing`.

!!! note "Advanced usage"
    This transform iterator is used for the internal calculations in `BiweightStats.jl`, which is why it has a somewhat complicated iterator implementation.


# Examples

```jldoctest transform
julia> X = randn(rng, 100);


julia> X[10] = 1e4 # add clear outlier
10000.0

julia> X[13] = NaN # add NaN
NaN

julia> X[25] = Inf # add Inf
Inf

julia> bt = BiweightTransform(X);

```

Lets confirm all the entries are finite. The iteration interface is divided into

```julia
(d, u2, flag), state = iterate(bt, [state])
```

where `d` is the data value minus `M`, `u2` is `(d / (c * MAD))^2`, and `flag` is whether the value is within the transformed dataset.

```jldoctest transform
julia> all(d -> isfinite(d[1]), bt)
true
```

and let's see how iteration differs between a normal sample and an outlier sample, which we manually inserted at index `10`-

```jldoctest transform
julia> (d, u2, flag), _ = iterate(bt, 9)
((-0.17093842061187192, 0.0009098761083851183, true), 10)

julia> (d, u2, flag), _ = iterate(bt, 10)
((0.0, 0.0, false), 11)
```

# References

[^1]: [NIST: biweight](https://www.itl.nist.gov/div898/software/dataplot/refman2/ch2/biweight.pdf)
