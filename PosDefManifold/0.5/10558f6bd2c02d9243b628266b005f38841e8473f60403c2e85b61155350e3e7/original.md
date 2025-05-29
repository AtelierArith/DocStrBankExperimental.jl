trade(P::ℍ{T}) where T<:RealOrComplex

Given a positive definite matrix `P`, return as a 2-tuple the  *trace* and the *determinant* of `P`.  This is used to plot positive matrices in two dimensions  (*TraDe plots*: log(trace/n) vs. log(determinant), see exemple here below).

`P` must be flagged by julia as `Hermitian`.   See [typecasting matrices](@ref).

**Examples**

```julia
using PosDefManifold
P=randP(3)
t, d=trade(P)  # equivalent to (t, d)=trade(P)

# TraDe plot
using Plots
k=100
n=10
𝐏=randP(n, k, SNR=1000); # 100 real Hermitian matrices
x=Vector{Float64}(undef, k)
y=Vector{Float64}(undef, k)
for i=1:k
    x[i], y[i] = trade(𝐏[i])
end
x=log.(x./n)
y=log.(y)
plot(x, y, seriestype=:scatter)
```
