```
expand_projectmatrices!(nep::Proj_SPMF_NEP, Wnew, Vnew)
```

The projected NEP is updated by adding the last column of `Wnew` and `Vnew` to the basis. Note that `Wnew` and `Vnew` contain also the "old" basis vectors. See also [`create_proj_NEP`](@ref)

# Example:

In the following example you see that the expanded projected problem has one row and column more, and the leading subblock is the same as the smaller projected NEP.

```julia-repl
julia> nep=nep_gallery("pep0"); n=size(nep,1);
julia> V=Matrix(1.0*I,n,2); W=Matrix(1.0*I,n,2);
julia> pnep=create_proj_NEP(nep);
julia> set_projectmatrices!(pnep,W,V);
julia> compute_Mder(pnep,0)
2×2 Array{Complex{Float64},2}:
 0.679107+0.0im   -0.50376+0.0im
 0.828413+0.0im  0.0646768+0.0im
julia> Vnew=[V ones(n)]
julia> Wnew=[W ones(n)]
julia> expand_projectmatrices!(pnep,Wnew,Vnew);
julia> compute_Mder(pnep,0)
3×3 Array{Complex{Float64},2}:
 0.679107+0.0im   -0.50376+0.0im  -12.1418+0.0im
 0.828413+0.0im  0.0646768+0.0im   16.3126+0.0im
 -17.1619+0.0im   -10.1628+0.0im   48.9481+0.0im
```
