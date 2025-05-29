```
project(M::Hyperbolic, p, X)
```

ミンコフスキー内積に関して、点 `p` の接空間に対して [`Hyperbolic`](@ref) 空間 `M` への直交射影を行います。

式は次のようになります。

$$
Y = X + ⟨p,X⟩_{\mathrm{M}} p,
$$

ここで、$⟨⋅, ⋅⟩_{\mathrm{M}}$ は埋め込み上の [`MinkowskiMetric`](@ref) を示し、[`Lorentz`](@ref) 多様体です。

!!! note
    射影は（デフォルトの）[`HyperboloidTVector`](@ref) 表現にのみ利用可能であり、他の表現にはそのような埋め込みはありません。

