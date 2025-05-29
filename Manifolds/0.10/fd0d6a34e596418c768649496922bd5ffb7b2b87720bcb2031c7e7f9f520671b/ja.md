```
log(M::Hyperbolic, p, q)
```

[`Hyperbolic`](@ref) 空間 $\mathcal H^n$ における対数写像を計算します。点 `p` から出発する接ベクトルが時間 1 で `q` に到達することを表します。式は $p ≠ q$ の場合次のようになります。

$$
\log_p q = d_{\mathcal H^n}(p,q)
\frac{q-⟨p,q⟩_{\mathrm{M}} p}{\lVert q-⟨p,q⟩_{\mathrm{M}} p \rVert_2},
$$

ここで $⟨⋅,⋅⟩_{\mathrm{M}}$ は埋め込み上の [`MinkowskiMetric`](@ref) を示し、[`Lorentz`](@ref) 型多様体です。$p=q$ の場合、対数写像はゼロベクトルに等しくなります。詳細については、例えば論文 [BergmannPerschSteidl:2016:1](@cite) の拡張版 [BergmannPerschSteidl:2015:1](@cite) を参照してください。
