```
E,A = companion(nep::PEP);
```

多項式固有値問題（PEP）を、MehrmannとVossの論文にあるように、伴随形式に線形化します。より正確には、n×nの係数行列を持つk次のPEPに対して、線形化された問題に対応する行列EとA（どちらもkn×kn）を返します。

$$
Ax = λEx
$$

# 例

```julia-repl
julia> pep = nep_gallery("pep0");
julia> E,A = companion(pep);
julia> λ, V = eigen(A,E);
julia> minimum(svd(compute_Mder(pep,λ[1])).S)
2.4845217786736996e-12
```

# 参考文献

  * V. Mehrmann and H. Voss, 非線形固有値問題、現代の固有値法への挑戦、GAMM‐Mitteilungen (2004)
