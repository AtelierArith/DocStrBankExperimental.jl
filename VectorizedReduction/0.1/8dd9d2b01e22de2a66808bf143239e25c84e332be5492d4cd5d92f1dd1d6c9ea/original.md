```
vmapreducethen(f, op, g, A::AbstractArray; dims=:, init)
```

Apply function `f` to each element of `A`, reduce the result over the dimensions `dims` using the binary function `op`, then apply `g` to the result. Equivalent to `g.(mapreduce(f, op, A, dims=dims, init=init))` but avoids the intermediate implied by said expression while also fusing the post-transform `g` such that the output array is populated in a single pass.

The reduction necessitates an initial value `init` which may be `<:Number` or a function which accepts a single type argument (e.g. `zero`); `init` is optional for binary operators `+`, `*`, `min`, and `max`.

# Examples

```jldoctest
julia> vmapreducethen(abs2, +, √, [1 2; 3 4], dims=1)    # L₂-norm; see `vnorm`
1×2 Matrix{Float64}:
 3.16228  4.47214

julia> vmapreducethen(abs2, +, √, [1 2; 3 4], dims=2, init=1000.0)
2×1 Matrix{Float64}:
 31.701734968294716
 32.01562118716424

julia> vmapreducethen(exp, +, log, [5 6; 7 8], dims=1)    # LSE, but recommend `vlogsumexp`
1×2 Matrix{Float64}:
 7.12693  8.12693
```
