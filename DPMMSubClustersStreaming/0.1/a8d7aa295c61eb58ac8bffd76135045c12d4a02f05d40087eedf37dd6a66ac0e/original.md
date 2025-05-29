```
 generate_mnmm_data(N::Int64, D::Int64, K::Int64, trials::Int64)
```

Generate `N` observations, generated from `K` `D` features Multinomial vectors, with `trials` draws from each vector.

Returns `(Samples, Labels, Vectors)`

# Example

```julia
julia> generate_mnmm_data(10000, 10, 5, 100)
...
```
