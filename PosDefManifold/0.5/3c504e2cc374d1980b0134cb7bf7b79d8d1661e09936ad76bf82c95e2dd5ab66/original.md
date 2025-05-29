```
	(1) fVec(f::Function, 𝐏::AnyMatrixVector;
	<
	w::Vector=[],
	✓w=false,
	allocs=[])
	>

	(2) fVec(f::Function, g::Function, 𝐏::AnyMatrixVector;
	< same optional keyword arguments in (1) >)
```

Given a 1d array $𝐏={P_1,...,P_k}$ of $k$ matrices  of the [𝕄Vector type](@ref), [𝔻Vector type](@ref), [𝕃Vector type](@ref) or  [ℍVector type](@ref) and an optional non-negative real weights vector  $w={w_1,...,w_k}$, return expression

$(1)\hspace{6pt}f_{i=1}^{k}(w_iP_i)$,

or

$(2)\hspace{6pt}f_{i=1}^{k}(w_ig(P_i))$,

where $f$ is either the `mean` or the `sum` standard julia functions  and $g$ is whatever matrix function  applying to each matrix $P_k$, such as `exp`, `log,`sqrt`, etc,  and [anonymous functions](https://docs.julialang.org/en/v1/manual/functions/#man-anonymous-functions-1).

This function is **multi-threaded**. It works by partitioning the $k$  operations required by the $f$ function in several groups,  passing each group to a separate thread and combining the result  of the intermediate operations.  This function allows a gain in computational time only when the number of  matrices (1) and/or their size (2) is high. Use `mean` and `sum` otherwise.  The maximal gain is obtained when the number of matrices in `𝐏` is an exact  multiple of the number of threads Julia is instructed to use.  For this latter, see [Threads](@ref).

!!! note "Nota Bene"

```
 Contrarily to Julia `mean` and `sum` function (v 1.1.0) the `fVec` function
 returns a matrix of the same type of the matrices in ``𝐏``.
```

*<optional keword argument>* `allocs` allows to pass pre-allocated memory  for holding the intermediate result of each thread.  Argument `allocs` must be a vector of as many matrices as threads and where  the matrices have the same dimension as the the matrices in $𝐏$  (see the example here below). Using this option is worthwhile only  if the size of the matrices is very high and/or when `fVec` is to be  called repeatedly on many vector of matrices, where the matrices  have always the same size, so that one allocation works for all calls.

If *<optional keyword argument>* `✓w=true` is passed, the weights are  normalized so as to sum up to 1, otherwise they are used as they are passed.  This option is provided to allow calling this function repeatedly without  normalizing the same weights vector each time. By default `✓w` is false.

**Examples**

```julia
using LinearAlgebra, PosDefManifold
Pset=randP(4, 1000); # generate 1000 positive definite 4x4 matrices
mean(Pset) # arithmetic mean calling Julia function
Threads.nthreads() # check how many threads are available
fVec(mean, Pset) # multi-threaded arithmetic mean

inv(mean(inv, Pset)) # Harmonic mean calling Julia function
inv(fVec(mean, inv, Pset)) # multi-threaded Harmonic mean

exp(mean(log, Pset)) # log Euclidean mean calling Julia function
exp(fVec(mean, log, Pset)) # multi-threaded log Euclidean mean

# notice that Julia `exp` function has changed the type of the result
# to `Symmetric`. To obtain an `Hermitian` output use
ℍ(exp(fVec(mean, log, Pset)))

w=(randn(1000)).^2
w=w./sum(w)  		# generate normalized random weights

# weighted arithmetic mean calling Julia function
sum(Pset[i]*w[i] for i=1:length(w))
# multi-threaded weighted arithmetic mean
fVec(sum, Pset, w=w)

# weighted harmonic mean calling Julia function
inv(sum(inv(Pset[i])*w[i] for i=1:length(w)))
# multi-threaded weighted harmonic mean
inv(fVec(sum, inv, Pset, w=w))

# pre-allocating memory
Pset=randP(100, 1000); # generate 1000 positive definite 100x100 matrices
Qset=MatrixVector(repeat([similar(Pset[1])], Threads.nthreads()))
fVec(mean, log, Pset, allocs=Qset)

# How much computing time we save ?
# (example min time obtained with 4 threads & 4 BLAS threads)
using BenchmarkTools
# standard Julia function
@benchmark(mean(log, Pset)) 					# (5.271 s)
# fVec
@benchmark(fVec(mean, log, Pset))				# (1.540 s)
```
