```julia
    (1) inductiveMean(metric::Metric, 𝐏::ℍVector)

    (2) inductiveMean(metric::Metric, 𝐏::ℍVector, q::Int, Q::ℍ)
```

**alias**: `indMean`

(1) Compute the Fréchet mean of 1d array $𝐏={P_1,...,P_k}$ of $k$ positive definite matrices of [ℍVector type](@ref) with a law of large number inductive procedure (Ho et *al.,* 2013; Lim and Palfia, 2019; Massart et *al.*, 2018)[🎓](@ref), such as

$G_1=P_1,$

$G_i=γ(i^{-1}, G_{(i-1)}, P_i), i=2,...,k,$

where $γ(i^{-1}, G_{(i-1)}, P_i)$ is a step on the [geodesic](@ref) relying $G_{(i-1)}$ to $P_i$ with arclength $i^{-1}$ using the specified `metric`, of type [Metric::Enumerated type](@ref).

(2) Like (1), but for the set of matrices $𝐐 ∪ 𝐏$, where it is assumed knowledge only of the set $𝐏$, the mean of $𝐐$ (Hermitian matrix argument `Q`) and the number of matrices in $𝐐$ (integer argument `q`). This method can be used, for example, for updating a block on-line algorithm, where $𝐏$ is the incoming block, `Q` the previous mean estimation and `q` the cumulative number of matrices on which the mean has been computed on-line.

For Fréchet means that do not have a closed form expression, this procedure features a computational complexity amounting to less than two iterations of gradient descent or fixed-point algorithms. This comes at the price of an approximation. In fact, the solution is not invariant to permutations of the matrices in array 𝐏 and convergence to the Fréchet mean for finite samples is not ensured (see Lim and Palfia, 2019; Massart et *al.*, 2018)[🎓](@ref).

Since the inductive mean uses the [`geodesic`](@ref) function, it is not available for the Von Neumann metric.

**Examples**

```julia
# A set of 100 matrices for which we want to compute the mean
𝐏=randP(10, 100)

𝐏1=ℍVector(collect(𝐏[i] for i=1:50)) # first 50
𝐏2=ℍVector(collect(𝐏[i] for i=51:100)) # last 50

# inductive mean of the whole set 𝐏
G=inductiveMean(Fisher, 𝐏)

# mean using the usual gradient descent algorithm
H, iter, conv=geometricMean(𝐏)

# inductive mean of 𝐏 given only 𝐏2,
# the number of matrices in 𝐏1 and the mean of 𝐏1
G2=inductiveMean(Fisher, 𝐏2, length(𝐏1), mean(Fisher, 𝐏1))

# average error
norm(G-H)/(dim(G, 1)^2)
norm(G2-H)/(dim(G, 1)^2)
```
