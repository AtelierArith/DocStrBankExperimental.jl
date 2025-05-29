```
function REP(A,roots,poles)
```

A `REP`-call creates a rational eigenvalue problem. The `REP` is defined by the sum $Σ_i A_i s_i(λ)/q_i(λ)$, where i = 0,1,2,..., all of the matrices are of size $n×n$ and $s_i$ and $q_i$ are polynomials. The constructor takes the roots and poles as input of polynomials with normalized highest coefficient. The NEP is defined as

$$
-λI+A_0+A_1\frac{p(λ)}{q(λ)}
$$

where `p` has the roots `roots` and `q` has the roots `poles`.

# Example

```julia-repl
julia> A0=[1 2; 3 4]; A1=[3 4; 5 6];
julia> nep=REP([A0,A1],[1,3], [4,5,6]);
julia> compute_Mder(nep,3)
2×2 Array{Float64,2}:
 Inf  Inf
 Inf  Inf
julia> (λ,x)=quasinewton(nep,v=[1;0])
(-0.3689603779201249 + 0.0im, Complex{Float64}[-2.51824+0.0im, 1.71283+0.0im])
julia> -λ*x+A0*x+A1*x*(λ-1)*(λ-3)/((λ-4)*(λ-5)*(λ-6))
2-element Array{Complex{Float64},1}:
 -2.5055998942313806e-13 + 0.0im
   1.318944953254686e-13 + 0.0im
```
