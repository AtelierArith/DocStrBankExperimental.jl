mplu(A::AbstractArray{TW,2}; TF=nothing, TR=nothing, residterm=residtermdefault,                     onthefly=nothing) where TW <: Real

Combines the constructor of the multiprecision array with the factorization. 

Step 1: build the MPArray. 

```
  (a) Store A and b in precision TW. 

  (b) Store the factorization (copy of A) in precision TF

  (c) Preallocate storage for the residual and a local copy of the
  solution in precision TR
```

Step 2: factor the low precision copy and return the factorization object

The `TR` kwarg is the residual precision. Leave this alone unless you know what you are doing. The default is `nothing` which tells the solver to set `TR = TW`. If you set `TR` it must be a higher precision than TW and you are essentially solving `TR.(A) x = TR.(b)` with IR with the factorization in `TF`. The MPArray structure stores the solution and the residual in precision `TR` and so the residual computation is done via `TR.(A) x`. The interprecision transfers are on the fly. So, the storage cost is the matrix, and the copy in the factorization precision.

The classic case is `TW = TF = Float32` and `TR = Float64`. The nasty part of this is that you must store TWO copies of the matrix. One for the residual computation and the other to overwrite with the factors. I do not think this is a good deal unless A is seriously ill-conditioned. My support for this is through `mplu`. To do this you must put the `TR` kwarg explicitly in your call to `mplu`.   

The kwarg `residterm` sets the termination criterion. `residterm == true` (default) terminates the iteration on small residuals.  `residterm == false` terminates the iteration on small normwise backward errors. Look at the docs for details.

You may not get exactly the same results for this example on different hardware, BLAS, versions of Julia or this package.  I am still playing with the termination criteria and the iteration count could grow or shrink as I do that.

## Example

```jldoctest
julia> using MultiPrecisionArrays.Examples

julia> n=31; alpha=Float32(1.0);

julia> G=Gmat(n, Float32);

julia> A = I + alpha*G;

julia> b = A*ones(Float32,n);

# use mpa with TF=TW=Float32 and TR=Float64

julia> AF = mplu(A; TF=Float32, TR=Float64, onthefly=true);

# Solve and save the iteration history

julia> mout = \(AF, b; reporting=true);

julia> mout.rhist
5-element Vector{Float64}:
 1.12500e+00
 1.74765e-07
 3.10862e-14
 6.66134e-16
 2.22045e-16

# What does this mean. I'll solve the promoted problem. TR.(A) x = b

julia> AD=Float64.(A);

julia> xd = AD\b;

julia> norm(xd - mout.sol,Inf)
1.11022e-15

# So IR with TR > TW solves a promoted problem.
```
