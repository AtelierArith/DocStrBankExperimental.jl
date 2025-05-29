```
kernel = diric(Ω::Real, n::Integer)
```

Dirichlet kernel, also known as periodic sinc function, where `n` should be a positive integer. Returns `sin(Ω * n/2) / (n * sin(Ω / 2))` typically, but `±1` when `Ω` is a multiple of 2π.

In the usual case where 'n' is odd, the output is equivalent to $1/n \sum_{k=-(n-1)/2}^{(n-1)/2} e^{i k Ω}$, which is the discrete-time Fourier transform (DTFT) of a `n`-point moving average filter.

When `n` is odd or even, the function is 2π or 4π periodic, respectively. The formula for general `n` is `diric(Ω,n) =``e^{-i (n-1) Ω/2}/n \sum_{k=0}^{n-1} e^{i k Ω}``, which is a real and symmetric function of`Ω`.

As of 2021-03-19, the Wikipedia definition has different factors. The definition here is consistent with scipy and other software frameworks.

# Examples

```jldoctest
julia> round.(diric.((-2:0.5:2)*π, 5), digits=9)'
1×9 adjoint(::Vector{Float64}) with eltype Float64:
 1.0  -0.2  0.2  -0.2  1.0  -0.2  0.2  -0.2  1.0

julia> diric(0, 4)
1.0
```
