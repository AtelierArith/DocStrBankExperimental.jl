```
random_itensor([rng=Random.default_rng()], [ElT=Float64], inds)
random_itensor([rng=Random.default_rng()], [ElT=Float64], inds::Index...)
```

Construct an ITensor with type `ElT` and indices `inds`, whose elements are normally distributed random numbers. If the element type is not specified, it defaults to `Float64`.

# Examples

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = random_itensor(i,j)
B = random_itensor(ComplexF64,undef,k,j)
```
