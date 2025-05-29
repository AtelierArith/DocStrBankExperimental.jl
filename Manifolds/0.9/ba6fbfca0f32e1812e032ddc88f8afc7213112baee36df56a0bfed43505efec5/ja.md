```
log(M::Hyperbolic, p, q)
```

[`Hyperbolic`](@ref) 空間 $\mathcal H^n$ における対数写像を計算します。点 `p` から出発する接ベクトルが、時間 1 で点 `q` に到達することを表します。式は $p ≠ q$ の場合次のようになります。

$$
\log_p q = d_{\mathcal H^n}(p,q)
\frac{q-⟨p,q⟩_{\mathrm{M}} p}{\lVert q-⟨p,q⟩_{\mathrm{M}} p \rVert_2},
$$

ここで $⟨⋅,⋅⟩_{\mathrm{M}}$ は埋め込み上の [`MinkowskiMetric`](@ref) を示し、[`Lorentz`](@ref) 多様体です。$p=q$ の場合、対数写像はゼロベクトルに等しくなります。 ```
