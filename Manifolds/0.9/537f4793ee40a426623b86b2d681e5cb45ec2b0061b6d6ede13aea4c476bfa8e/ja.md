```
project(M::AbstractProjectiveSpace, p)
```

点 `p` を埋め込みから [`AbstractProjectiveSpace`](@ref) `M` への直交射影します：

$$
\operatorname{proj}(p) = \frac{p}{\lVert p \rVert}_{\mathrm{F}},
$$

ここで、$\lVert ⋅ \rVert_{\mathrm{F}}$ はフロベニウスノルムを示します。これは [`AbstractSphere`](@ref) への射影と同じです。
