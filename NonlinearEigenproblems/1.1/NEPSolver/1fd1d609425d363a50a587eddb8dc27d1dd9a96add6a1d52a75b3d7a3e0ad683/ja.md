```
λ,v = newtonqr([eltype],nep::NEP;[errmeasure,][tol,][maxit,][λ,][v,][c,][logger])
```

この関数は、参考文献に記載されたようにニュートン-QR法を実装しています。この方法は、$M(λ)$のランクを明らかにするQR因子分解の計算を含み、収束時に上三角行列$R$の最後の対角要素$R[n,n]$が$M(λ)$が特異になる結果としてゼロになるという考えに基づいています。QR因子分解の計算は高コストであるため、小規模な問題やQR計算をより安価にする特定の構造を持つ問題に対してこの方法を使用することをお勧めします。他のパラメータについては[`augnewton`](@ref)を参照してください。

# 例

```julia-repl
julia> nep=nep_gallery("pep0")
julia> λ,v=newtonqr(nep,v=ones(size(nep,1)));
julia> norm(compute_Mlincomb(nep,λ,v))/norm(v)
8.440206093655014e-15
```

# 参考文献

  * Kublanovskaya, V. N., (1970).  λ行列の一般化された固有値問題の解法へのアプローチについて, SIAM J. Numer. Anal. 7, 532–537
  * Güttel, S., & Tisseur, F. (2017). 非線形固有値問題. Acta Numerica, 26, 1-94. doi:10.1017/S0962492917000034
