```julia
function genPerms(stat::BivStatistic, x::UniData, 
            ns::Int, direction::TestDir, design::Assign) 
    
function genPerms(stat::IndSampStatistic, x::UniData, 
            ns::Vector{Int}, direction::TestDir, design::Assign)
                
function genPerms(stat::RepMeasStatistic, x::UniData, 
            ns::@NamedTuple{n::Int, k::Int}, direction::TestDir, design::Assign)
            
function genPerms(stat::OneSampStatistic, x::UniData, 
            ns::Int, direction::TestDir, design::Assign)

    where {TestDir<: TestDirection, Assign <: Assignment}
```

Generate a *lazy* iterator over all possible (systematic) permutations according to the permutation scheme  to be used for test statistic `stat`, which is given as a singleton of type [Statistic](@ref).

Note that data permutation in *PermutationsTests.jl* are always obtained by lazy iterators, that is, permutations are never listed physically. This is one of the main reasons why the package is fast and allocates little memory.

You do not need these functions for general usage of the package, however you need to know them  if you wish to [create your own test](@ref "Create your own test"). 

There exists a permutation scheme for each [group](@ref "Statistic groups") the test statistics `stat` belong to.

`x` is the [`membership`](@ref) vector.

For the `ns` argument see [ns](@ref).

`direction` is a singleton of type [TestDirection](@ref).

`design` is a singleton of type [Assignment](@ref). In order to avoid errors,  use the result of [`assignment`](@ref) as argument `design`. 

With `stat` a `BivStatistic` (*e.g.*, `PearsonR()`), the iterations unfold the $N!$ possible reorderings of the  $N$ elements in vector `x` and argument `ns` is ignored. In this case `x` is either a trend (e.g., [1,...,N]  for a linear trend) or a variable to be permuted for correlation/trend tests.

With `stat` a `IndSampStatistic` (*e.g.*, `AnovaF_IS()`), the iterations unfold the  $\frac{N!}{N_1 \cdot \ldots \cdot N_K}$ possible arrangements of $N$ elements in $K$ groups.  In this case `x` is ignored and `ns` is a vector holding the K group  numerosities (i.e., [N1,...,Nk]). For this scheme, if the design is balanced, *i.e.*, all elements of ns are equal,  some permutations are redundant, see [`nrPerms`](@ref).

With `stat` a `RepMeasStatistic` (*e.g.*, `AnovaF_RM()`), the iterations unfold the $(K!)^N$ reordering of $K$ measures  (e.g., treatments) in all $N$ observation (e.g., subjects). In this case `x` is ignored and `ns` is a  [named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types) with form `(n=N, k=K)`. For this scheme, if the test is bi-directional some permutations are redundant, see [`nrPerms`](@ref).

With `stat` a `OneSampStatistic` (*e.g.*, `StudentT_1S()`), the iteartions unfold the $2^N$ flip-sign patterns.  In this case `x` is ignored and `ns=N`, where $N$ is the number of observations.

!!! note "nota bene"
    Only for `stat` belonging to the `OneSampStatistic` group,  the iterator generates tuples and not arrays (see examples below).


!!! tip "keep in mind"
    Regardless the permutation scheme, the first generated iteration always correspons to the "permutation" of the data as it has been observed (that is, the only permutation that actually does not permute the data).


*Examples*

```julia
using PermutationsTests

x=membership(PearsonR(), 3) # -> [1, 2, 3]
# The observations are always listed in the natural order 1, 2,...
Pr = genPerms(PearsonR(), x, 0, Both(), Balanced()) 
collect(Pr) # physically list the iterations
# yields the 6 = 3! elements [1, 2, 3]...[3, 2, 1]
# Here the integers represent the permuted position of the obervations in x

PfIS = genPerms(AnovaF_IS(), Int[], [2, 3], Both(), Unbalanced()) 
collect(PfIS)
# yields the 10 = 5!/2!3! elements [1, 1, 2, 2, 2]...[2, 2, 2, 1, 1]
# Here the integers represent the permuted group to which the corresponding 
# obervations in the data vector `y` belongs. see `_permTest!`.
# If the design is balanced and the test is bi-directional, 
# only 1/k! of the permutations are retained, thus 
PfIS_ = genPerms(AnovaF_IS(), Int[], [2, 2], Both(), Balanced()) 
collect(PfIS_) 
# yields the 3 = (4!/2!2!)/2! elements [1, 1, 2, 2], [1, 2, 2, 1] and [2, 1, 2, 1]

PfRM = genPerms(AnovaF_RM(), Int[], (n=2, k=3), Right(), Balanced()) 
collect(PfRM)
# yields the 36 = (k!)^n elements [1, 2, 3, 4, 5, 6], [1, 3, 2, 4, 5, 6], 
# ..., [3, 2, 1, 6, 5, 4]
# Here the integers represent the treatement for each subject to which the 
# corresponding obervation in the data vector `y` belongs. see `_permTest!`.
# If the test is bi-directional, 
# only 1/k! of the permutations are retained, thus 
PfRM_ = genPerms(AnovaF_RM(), Int[], (n=2, k=3), Both(), Balanced()) 
collect(PfRM_)
# yields instead the 6 = (k!)^n / elements [1, 2, 3, 4, 5, 6], [1, 3, 2, 4, 5, 6], 
# ..., [3, 2, 1, 4, 5, 6]

Pt1S = genPerms(StudentT_1S(), Int[], 3, Both(), Balanced())
collect(Pt1S)
# yields the 8=2^3 elements (1, 1, 1), (-1, 1, 1), (1, -1, 1), (-1, -1, 1), 
#..., (-1, -1, -1) 
# Here the integers represent the sign to be applied to each observation 
# at each data permutation. 
# Note that only for OneSampStatistic, the iterator generates tuples and not arrays.
```
