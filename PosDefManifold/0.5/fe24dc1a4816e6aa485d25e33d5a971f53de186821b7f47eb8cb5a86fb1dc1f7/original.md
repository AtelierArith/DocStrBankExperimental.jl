```
(1) regularize!(P::ℍ; <SNR=10e3>)
(2) regularize!(𝐏::ℍVector; <SNR=10e3>)
```

Add [white noise](https://bit.ly/2TN8472) to either

  * (1) a positive definite matrix $P$ of size $n⋅n$, or
  * (2) a 1d array $𝐏$ of $k$ positive definite matrices of size $n⋅n$, of [ℍVector type](@ref).

The added noise improves the matrix conditioning with respect to inversion.  This is used to avoid numerical errors when decomposing these matrices  or when evaluating some functions of their eigevalues such as the log.

A constant value is added to all diagonal elements of (1) $P$  or (2) af all matrices in $𝐏$,  that is, on output:

$\textrm{(1)}\hspace{2pt}P\leftarrow P+ηI$

$\textrm{(2)}\hspace{2pt}𝐏_i\leftarrow 𝐏_i+ηI, \hspace{2pt}\textrm{for}\hspace{2pt} i=1:k.$

The amount of added noise $η$ is determined by the `SNR`  *<keyword argument>*, which by default is 10000. This is  such that

$\textrm{(1)}\hspace{2pt}SNR=\frac{\displaystyle\textrm{tr}(P)}{\displaystyle\textrm{tr}(ηI)}.$

$\textrm{(2)}\hspace{2pt}SNR=\frac{\displaystyle\sum_{i=1}^{k}\textrm{tr}(𝐏_i)}{\displaystyle k\hspace{1pt}\textrm{tr}(ηI)}.$

$P$ in (1) must be flagged as Hermitian. See [typecasting matrices](@ref).

!!! note "Nota Bene"
    The keyword argument `SNR` expresses a SNR ([signal-to-noise ratio](https://bit.ly/1VvpvnQ)), and is not expressed in decibels,  but as the SNR variance ratio. It must be a positive number. Differently from function `randΛ`[`randEigvalsMat`](@ref), `randλ`[`randEigvals`](@ref) and `randP`[`randPosDefMat`](@ref), the SNR here is not the expected SNR, but the actual SNR.


**See also**: `randP` ([`randPosDefMat`](@ref)).

**Examples**

```julia
# (1)
using LinearAlgebra, Plots, PosDefManifold
n=3
U=randU(n)
# in Q we will write two matrices,
# the unregularized and regularized matrix side by side
Q=Matrix{Float64}(undef, n, n*2)
P=ℍ(U*Diagonal(randn(n).^2)*U') # generate a real 3x3 positive matrix
for i=1:n, j=1:n Q[i, j]=P[i, j] end
regularize!(P, SNR=5)
for i=1:n, j=1:n Q[i, j+n]=P[i, j] end # the regularized matrix is on the right
heatmap(Matrix(Q), yflip=true, c=:bluesreds)

# (2)
𝐏=[ℍ(U*Diagonal(randn(3).^2)*U') for i=1:5] # 5 real 3x3 positive matrices
regularize!(𝐏, SNR=1000)

## Run a test
using LinearAlgebra
𝐏=randP(10, 100, SNR=1000); # 100 real Hermitian matrices
signalVar=sum(tr(P) for P in 𝐏);
regularize!(𝐏, SNR=1000);
signalPlusNoiseVar=sum(tr(P) for P in 𝐏);
output_snr=signalVar/(signalPlusNoiseVar-signalVar)
# output_snr should be approx. equal to 1000
```
