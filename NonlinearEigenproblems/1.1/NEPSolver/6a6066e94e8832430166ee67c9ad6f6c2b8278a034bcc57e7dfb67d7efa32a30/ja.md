```
λ,v = polyeig([eltype],nep::ChebPEP)
```

Chebyshev基底で表現されたNEPの伴随線形化を計算し、固有対を返します。

# 例

```julia
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> chebpep=ChebPEP(nep,9,-3,1,cosine_formula_cutoff=5);
julia> (λv,V)=polyeig(chebpep);
julia> ii=argmin(abs.(λv));
julia> λ=λv[ii];
julia> v=V[:,ii];
julia> norm(compute_Mlincomb(chebpep,λ,v))
1.3543968603949142e-14
julia> # 実際、元のNEPに対する悪くない近似です
julia> norm(compute_Mlincomb(nep,λ,v))
4.326355966047557e-6
```

[`ChebPEP`](@ref)も参照してください。

# 参考文献:

  * Amiraslani, A., Corless, R. M. & Lancaster, P. "多項式基底で表現された行列多項式の線形化" IMA J. Numer. Anal.,29 (2009): 141–157.
  * Effenberger and Kressner. "非線形固有値問題のためのチェビシェフ補間." BIT Numerical Mathematics 52.4 (2012): 933-951.
