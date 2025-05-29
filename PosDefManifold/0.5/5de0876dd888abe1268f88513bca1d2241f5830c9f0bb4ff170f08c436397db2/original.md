```
    (1) randEigvalsMat(n::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3 >)

    (2) randEigvalsMat(n::Int, k::Int;
    < same keyword arguments as in (1) >)
```

**alias**: `randΛ`

(1) Generate an $n⋅n$ diagonal matrix of random real positive eigenvalues.

(2) An array 1d (of [𝔻Vector type](@ref)) of $k$ matrices of the kind in (1)

The eigenvalues are generated according to model

$λ_i=χ_{df}^2+η,\hspace{6pt}\textrm{for}\hspace{2pt}i=1:n,$

where

  * $χ_{df}^2$ (signal term) is randomly distributed as a [chi-square](https://bit.ly/1IXkulE) with `df` degrees of freedom,
  * $η$ is a [white noise](https://bit.ly/2TN8472) term, function of *<keyword argument>* `eigvalsSNR`, such that

$\textrm{eigenvalues SNR}=\mathbb{E}\big(\sum_{i=1}^{n}λ_i\big)\big/nη.$

The expected sum $\mathbb{E}\big(\sum_{i=1}^{n}λ_i\big)$ here above is the  expected variance of the signal term, i.e., $n(df)$, since the expectation  of a random chi-squared variable is equal to its degrees of freedom.

If `eigvalsSNR=Inf` is passed as argument, then $η$ is set to zero, *i.e.*,  no white noise is added. In any case `eigvalsSNR` must be positive.

Note that with the default value of *<keyword argument>* `df` (`df=2`)  the generating model assumes that the eigenvalues  have exponentially decaying variance, which is often observed on real data.

!!! note "Nota Bene"
    The *<keyword argument>* `eigvalsSNR` expresses the expected eigenvalues SNR ([signal-to-noise ratio](https://bit.ly/1VvpvnQ)), not the real one, and is not expressed in decibels, but as the expected SNR variance ratio.


This function is used by function `randP` ([`randPosDefMat`](@ref)) to generate  random positive definite matrices with added white noise in order  to emulate eigenvalues observed in real data and to  improve the conditioning of the generated matrices with respect to inversion.

**See also**: `randλ` ([`randEigvals`](@ref)), `randU` ([`randUnitaryMat`](@ref)),  `randP` ([`randPosDefMat`](@ref)), `randχ²` ([`randChi²`](@ref)).

**Examples**

```julia
using PosDefManifold
# (1)
n=3;
U=randU(n);
Λ=randΛ(n, eigvalsSNR=100)
P=U*Λ*U' # generate an SPD matrix
using LinearAlgebra
Q=ℍ(U*Λ*U') # generate an SPD matrix and flag it as 'Hermitian'

# (2) generate an array of 10 matrices of simulated eigenvalues
Dvec=randΛ(n, 10)
```
