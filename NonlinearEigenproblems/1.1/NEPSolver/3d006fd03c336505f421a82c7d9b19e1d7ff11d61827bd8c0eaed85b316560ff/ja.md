```
λ,v = implicitdet([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger])
```

この関数は、参考文献のアルゴリズム4.3に基づいて、暗黙の行列式法を実装しています。この方法は、$det(M(λ))/det(G(λ)) = 0$という方程式にニュートン-ラフソン法を適用します。ここで、$G(λ)$は鞍点行列で、$M(λ)$は(1,1)ブロックにあります。$G(λ)$の(2,1)および(1,2)ブロックはそれぞれ$c^H$と$c$に設定されています。$M(λ)$が特異であっても、$G(λ)$は特異でない場合があることに注意してください。詳細については参考文献を参照してください。他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=implicitdet(nep,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
2.566371972986362e-14
```

# 参考文献

  * Spence, A., & Poulton, C. (2005). Photonic band structure calculations using nonlinear eigenvalue techniques, J. Comput. Phys., 204 (2005), pp. 65–8
  * Güttel, S., & Tisseur, F. (2017). The nonlinear eigenvalue problem. Acta Numerica, 26, 1-94. doi:10.1017/S0962492917000034
