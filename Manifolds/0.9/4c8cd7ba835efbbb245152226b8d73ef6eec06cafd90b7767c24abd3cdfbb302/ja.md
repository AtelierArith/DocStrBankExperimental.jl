```
project(M::AbstractProjectiveSpace, p, X)
```

点 `X` を [`AbstractProjectiveSpace`](@ref) `M` の点 `p` における接空間に直交的に射影します：

$$
\operatorname{proj}_p (X) = X - p⟨p, X⟩_{\mathrm{F}},
$$

ここで、$⟨⋅, ⋅⟩_{\mathrm{F}}$ はフロベニウス内積を示します。実数の [`AbstractSphere`](@ref) と `AbstractProjectiveSpace` において、この射影は同じです。
