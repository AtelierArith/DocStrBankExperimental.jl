```
λ,v = polyeig([eltype],nep::PEP,[eigsolvertype,])
```

多項式固有値問題（PEP）を伴随形式に線形化し、対応する線形固有値問題を解決します。詳細は[`companion`](@ref)を参照してください。`eigsolvertype`はオプションで、線形問題の解決方法を指定するために使用できます。詳細は[`eig_solve`](@ref)および[`EigSolver`](@ref)を参照してください。

# 例

```julia-repl
julia> pep = nep_gallery("pep0");
julia> λ,V = polyeig(pep);
julia> minimum(svd(compute_Mder(pep,λ[1])).S)
1.2050763381899922e-14
julia> norm(compute_Mlincomb(pep,λ[2],vec(V[:,2])))
1.0245470569036458e-12
```
