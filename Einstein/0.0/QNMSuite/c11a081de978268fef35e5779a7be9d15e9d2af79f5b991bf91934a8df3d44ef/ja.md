```
A, E = qnm_pep_companion(TFC, pep::AbstractVector{<:AbstractMatrix}) where TFC <: Union{AbstractFloat, Complex{<:AbstractFloat}}
```

多項式固有値問題（PEP）を線形化し、MehrmannとVossの論文にあるように伴随行列形式を返します。より正確には、n×nの係数行列を持つk次のPEPに対して、線形化された問題に対応するkn×knの行列AとEを返します。

$$
Ax = λEx
$$

# 参考文献

  * [mehrmann2004nonlinear](@citet*)
  * [NonlinearEigenproblems.jl/src/method_companion.jl at master · nep-pack/NonlinearEigenproblems.jl](https://github.com/nep-pack/NonlinearEigenproblems.jl/blob/master/src/method_companion.jl)
