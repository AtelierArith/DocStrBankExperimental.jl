mpglu(A::AbstractArray{TW,2}; TF=Float32, TR=nothing,      residterm=residtermdefault1, basissize=10) where TW <: Real

Combines the constructor of the multiprecision GMRES-ready array with the factorization.

Step 1: build the MPGArray

```
  (a) Store A and b in precision TW.

  (b) Store the factorization (copy of A) in precision TF

  (c) Preallocate storage for the residual, a local copy of the
  solution, and the Krylov vectors in precision TR
```

Step 2: Call mpglu! to build the factorization object

The `TR` kwarg is the residual precision. Leave this alone unless you know what you are doing. The default is `nothing` which tells the solver to set `TR = TW`. If you set `TR` it must be a higher precision than TW and you are essentially solving `TR.(A) x = TR.(b)` with IR with the factorization in `TF`.

The case of interest here is `TW = Float32; TF = Float16; TR = Float64`. IR-GMRES with those precisions is sometimes the savior of half precision.

The default basis size is 10. You can (and should) play with that if you are not happy with the results. If you are having trouble storing enough vectors, IR-BiCGSTAB `mpblu` is worth a shot.

Take this example, please.

You may not get exactly the same results for this example on different hardware, BLAS, versions of Julia or this package.  I am still playing with the termination criteria and the iteration count could grow or shrink as I do that.

## Example

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

# Can Float16 be saved? How 'bout IR-GMRES?

julia> GF=mpglu(A; TR=Float64);

julia> mout3=\(GF, b; reporting=true);

julia> mout3.rhist
6-element Vector{Float64}:
 9.88750e+01
 2.23211e-04
 9.61252e-09
 1.26477e-12
 8.10019e-13
 8.66862e-13

# Shazam! Did we get the solution of the promoted problem?

julia> xp=Float64.(A)\b; norm(xp-mout3.sol,Inf)
9.43157e-12

# Yup.

```
