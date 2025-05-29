```julia
function statistic(x::IntVec, y::UniData, stat::AnovaF_IS; 
                k::Into=nothing, 
                ns::Union{Vector{Int}, Nothing}=nothing, 
                kwargs...) 
```

*F* statistic of the 1-way ANOVA for independent samples, see [Edgington (1995)](@ref "References"), p. 60. 

The data is given as an unique vector `y`, holding the observations for each group in the natural order, thus for $K$ groups `y` holds $N=N_1+ \ldots +N_K$ elements, where $N_k$ is the number of observations  for the $k^{th}$ group.

`x` is the [`membership(::IndSampStatistic)`](@ref) vector.

`k` is the number of groups (independent samples). If omitted it will be computed.

`ns` is the group numerosity vector with form `ns=[N1,..., NK]`. If omitted it will be computed.

*Examples*

```julia
using PermutationTests
g1=[1.0, 2.0, 3.0, 4.0] # observations for group 1 
g2=[1.1, 2.8, 3.2, 4.4, 5.3] # observations for group 2 
ns=[length(g1), length(g2)] # N1, N2
y=vcat(g1, g2)
x=membership(AnovaF_IS(), ns)
F=statistic(x, y, AnovaF_IS())
# or, to avoid finding k and ns from y
F2=statistic(x, y, AnovaF_IS(); k=2, ns=ns)

# The square of the t test statistic for independent samples for a bi-directional test
# is equal to the above F test statistics

t=statistic(x, y, StudentT_IS(); ns=ns)
println(t^2≈F ? "OK" : "error")

```
