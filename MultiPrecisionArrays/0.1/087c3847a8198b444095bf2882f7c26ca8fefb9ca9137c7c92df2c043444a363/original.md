mpblu(A::AbstractArray{TW,2}; TF=Float32, TR=nothing, i           residterm=residtermdefault) where TW <: Real

Combines the constructor of the multiprecision BiCGSTAB-ready array with the factorization.

Step 1: build the MPBArray

Step 2: Call mpblu! to build the factorization object

Step 3: Allocate the internal vectors that BiCGSTAB needs.

IR-Krylov methods were designed as saviors of half precision. So, as we did with mpglu, we will run through some examples. The difference here is that there is no Kylov basis to store. 

Here's the example from `mpglu`

You may not get exactly the same results for this example on different hardware, BLAS, versions of Julia or this package.  I am still playing with the termination criteria and the iteration count could grow or shrink as I do that.

#Example

```jldoctest
julia> using MultiPrecisionArrays

julia> using MultiPrecisionArrays.Examples

julia> N=4096; alpha=799.0; AD = I - alpha*Gmat(N); A = Float32.(AD);

# Try vanilla IR with TF=Float16

julia> xe=ones(Float32,N); b=A*xe; AF=mplu(A);

julia> mout=\(AF, b; reporting=true);

julia> mout.rhist
5-element Vector{Float64}:
 9.88750e+01
 3.92435e+00
 3.34373e-01
 2.02045e-01
 2.24720e-01

# That does not look like convergence. What about TR=Float64?

julia> BF=mplu(A; TR=Float64);

julia> mout2=\(BF, b; reporting=true);

julia> mout2.rhist
5-element Vector{Float64}:
 9.88750e+01
 3.92614e+00
 3.34301e-01
 2.01975e-01
 2.24576e-01

# This is where we were in the docs for ```mpglu```. I'll try IR-BiCGSTAB

julia> GF=mpblu(A; TR=Float64);

julia> mout3=\(GF, b; reporting=true);

julia> mout3.rhist
4-element Vector{Float64}:
 9.88750e+01
 2.16858e-11
 8.38440e-13
 8.81073e-13

# That is very different from IR-GMRES. The reason is that there is no
# limit on Krylov iterations because there is no Krylov subspace.
# So, the linear work produces a large reduction in the residual in
# the first iterate.

# Of course, we got it right and solved the promoted problem.

julia> xp=Float64.(A)\b; norm(xp-mout3.sol,Inf)
1.63376e-11
```
