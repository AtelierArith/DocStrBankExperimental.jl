```julia
function statistic(x::IntVec, y::UniData, stat::AnovaF_RM; 
                ns::@NamedTuple{n::Int, k::Int}, 
                ∑Y²kn::Realo=nothing, 
                ∑y²::Realo=nothing, 
                ∑S²k::Realo=nothing, 
                kwargs...) 
```

*F* statistic of 1-way ANOVA for repeated measures, see [Edgington (1995)](@ref "References"), p. 102. 

The data is given as an unique vector `y` concatenaning the $N$ observations for the $K$ measures  (treatments, time, ...) in the natural order, that is, the $K$ treatments for observation 1, ...,  the $K$ tratments for observation $N$. Thus, `y` holds $N \cdot K$ elements. 

`x` is the [`membership(::RepMeasStatistic)`](@ref) vector.

`ns` is a julia [named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types)  with form `(n=N, k=K)` (see examples below).

`∑Y²kn`, `∑y²` and `∑S²k` can be optionally provided to speed up computations since these quantities are invariant by data permutations. The exported function `_∑Y²kn_∑y²_∑S²k` can be used for this purpose,  see the examples below. 

*Examples*

```julia
using PermutationTests
# K=2 (measurements), N=4 (observations)
o1=[1.0, 2.0]; # first observation 
o2=[2.0, 2.8]; # second observation 
o3=[3.0, 2.6]; # third observation
o4=[4.0, 4.1]; # fourth observation
ns=(n=4, k=2); # four obs. and two measurements
y=vcat(o1, o2, o3, o4);
x=membership(AnovaF_RM(), ns);
F=statistic(x, y, AnovaF_RM(); ns=ns)

# pre-compute some data
pcd=_∑Y²kn_∑y²_∑S²k(y, ns);
F2=statistic(x, y, AnovaF_RM(); ns=ns, ∑Y²kn=pcd[1], ∑y²=pcd[2], ∑S²k=pcd[3])

# The t test statistic for repeated measures is the same as the one-sample 
# t test statistic on the difference of the two measurements. 
# The square of those statistics for a bi-directional test are equal to 
# the above F test statistics. 

x=membership(StudentT_1S(), ns.n)
t=statistic(x, y[1:2:ns.n*2-1].-y[2:2:ns.n*2], StudentT_1S())
println(t^2≈F ? "OK" : "error")

```
